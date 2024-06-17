<h1>Nginx Configuration</h1>
<p>Nginx is a reverse proxy and load balancing web server that is used to handle incoming http requests.  The following procedures are to be followed when installing Nginx from command line on a Linux web server.  <br><br><b><em>Note - logged in user must have root privileges in order to install Nginx.</em></b></p>

<h2>SSL Certificate</h2>
<p>Prior to Nginx installation it is required that an SSL certificate be applied to the host to ensure proper encryption and enable https traffic.  What type of certificate will depend on whether the host is behind the firewall or reachable by public internet in the DMZ.  If behind the firewall, a SSL certificate from the City's internal certificate authority will be sufficient.  Otherwise, an SSL certificate from an external CA such as GoDaddy will be required.  In either case the Datacenter team will help with the aquisition of such certificate and Network will also need to update the internal DNS when applicable.</p>

<p>The following assumes the certificate file provided by Datacenter is in .pem format with private key and certificate block contained within the same file.  Exact steps may vary depending on the format of the certifcate file.</p>


```bash
# Split the .pem file into separate private key and certificate block files.  
# From the directory containing the original .pem file - run the following command to create a new private key file from the combined .pem file:
openssl pkey -in originalpemfile.pem -out yournewkey.pem
```


```bash
# Use the following command to create a new certificate block file using openssl:
openssl x509 -in originalpemfile.epm -out yournewcert.pem
```


<p>Move the newly created private key and certificate files to the appropiate locations.</p>


```bash
# Create directory for private key then copy key file to newly created directory
sudo mkdir /etc/ssl/keys
sudo mv yournewkey.pem /etc/ssl/keys
```


```bash
# Copy certificate file to appropriate location.  The certs directory will exist already and will not need to be created:
sudo mv yournewcert.pem /etc/ssl/certs
```

<h2>Nginx Installation and Configuration</h2>  
<p>Nginx will be installed using apt package manager.  Once installed, a configuration file will need to be created as well as enabled.</p>


```bash
# Update the package lists for upgrades and new packages
sudo apt update
sudo apt install nginx
```


```bash
# Navigate to the /etc/nginx/sites-available directory. 
# Create a new Nginx config file using the same naming convention of the host.  
# For example: if the host name is COFASV38 the config file will also be named COFASV38:
cd /etc/nginx/sites-available
sudo nano cofasv38
```


<p>An empty file will be opened in the text editor.</p>


```bash
# Use the following server block configuration - updating the hostname to the appropriate name.  
# When finished, save the file and close the text editor:
server {
  server_name hostname.franklintn.gov;
  access_log /var/log/nginx/access.log;
  error_log /var/log/nginx/error.log;

  listen 443 ssl; # Listen on port 443 SSL
  ssl_certificate /etc/ssl/certs/yournewcert.pem; # Path to newly added certificate file
  ssl_certificate_key /etc/ssl/keys/yournewkey.pem; # Path to newly added key file

  client_max_body_size 10M; # Optional. Increases the permitted body size of an http request - mostly necessary for handling attachments

  root /var/www/html; # Default path to the root directory of the website
  index index.html index.htm index.nginx-debian.html; # Types of files Nginx will attempt to serve at the root
}
```


<p>When the new config file is created - it is necessary to create a symbolic link (symlink) between the new file in /etc/nginx/sites-available and /etc/nginx/sites-enabled in order to utilize the config file.  It will also be necessary to remove the existing symlink created for the default config file that is created during the Nginx installation process.</p>


```bash
# Remove the existing default symlink.
# Replace with symlink to newly created config file:
cd /etc/nginx/sites-enabled
sudo rm default
sudo ln -s /etc/nginx/sites-available/cofasv38 # Replace cofasv38 with the appropriate config file name

# Test the config file
sudo nginx -t
```


<h2>UFW</h2>
<p>UFW - Uncomplicated Firewall - is utilized by Nginx to permit or deny network traffic to specific ports.  By default, UFW is not enabled when Nginx is installed.  It is necessary to enable UFW and create new rules to allow network traffic only from specific ports to better prevent against malicious actors.</p>


```bash
# Create UFW rule to allow port 22.  
# Port 22 is used for SSH connection and is important to allow traffic to when first enabling UFW:
sudo ufw allow 22/tcp
```


```bash
# Create UFW rule allowing https traffic via port 443.
# Enable firewall:
sudo ufw allow 443/tcp
sudo ufw enable
```


<p>You should now have an enabled firewall allowing traffic only to ports 22 (for SSH) and 443 (for SSL)</p>


```bash
# Enter the following command to confirm UFW is properly applied:
sudo ufw status

# The terminal should look something like this:
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere                  
443/tcp                    ALLOW       Anywhere                  
22/tcp (v6)                ALLOW       Anywhere (v6)             
443/tcp (v6)               ALLOW       Anywhere (v6) 
```


<h2>Final Steps and Testing</h2>
<p>You should now have SSL certificate and private key in place, Nginx installed with config file created and symlink enabled, and generated UFW rules with firewall enabled.  We are now ready to test the configuration.</p>

```bash
# Restart the Nginx service to allow for the new config file to be applied
sudo systemctl restart nginx
```

<p>You should now be able to test the Nginx configuration by visiting https://hostname.franklintn.gov/ in browser to see if the default Nginx landing page located at /var/www/html/index.nginx-debian.html is available.</p>
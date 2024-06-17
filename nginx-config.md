<h1>Nginx Configuration</h1>
<p>Nginx is a reverse proxy and load balancing web server that is used to handle incoming http requests.  The following procedures are to be followed when installing Nginx from command line on a Linux web server. <b>Note - logged in user must have root privileges in order to install Nginx.</b></p>

<h2>SSL Certificate</h2>
<p>Prior to Nginx installation it is required that an SSL certificate be applied to the host to ensure proper encryption and https traffic.  What type of certificate will depend on whether the host is behind the firewall or reachable by public internet in the DMZ.  If behind the firewall, a SSL certificate from our internal certificate authority will be sufficient.  Otherwise, a SSL certificate from an external CA such as GoDaddy will be required.  In either case the Datacenter team will help with the aquisition of such certificate and Network will also need to update the internal DNS.</p>

<p>The following assumes the certificate file is in .pem format with private key and certificate block contained within the same file.  Exact steps may vary depending on the format of the certifcate file provided by Datacenter.</p>

```bash
# Split the .pem file into separate private key and certificate block files.  From the directory containing the .pem file run the following command to create a new private key file from the combined .pem file:
openssl pkey -in originalpemfile.pem -out yournewkey.pem
```

```bash
# Use the following command to create a new certificate block file using openssl:
openssl x509 -in originalpemfile.epm -out yournewcert.pem
```

<p>Copy the newly created private key and certificate files to the appropiate locations.</p>

```bash
# Create directory for private key then copy file to newly created directory
sudo mkdir /etc/ssl/keys
sudo mv yournewkey.pem /etc/ssl/keys
```

```bash
# Copy certificate file to appropriate location.  The certs directory will not need to be created:
sudo mv yournewcert.pem /etc/ssl/certs
```

```bash
# Update the package lists for upgrades and new packages
sudo apt update
sudo apt install nginx
```

```bash
# Navigate to the /etc/nginx/sites-available directory to create a new Nginx config file using the naming convention of the host.  For example: if the host name is COFASV38 the config file will also be named COFASV38
cd /etc/nginx/sites-available
sudo nano cofasv38
```

<p>An empty file will be opened in the text editor.</p>
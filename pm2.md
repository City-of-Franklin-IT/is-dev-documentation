<h1>PM2 Process Manager</h1>
<p>Node applications served on a Linux server utilize PM2 process manager in order to automatically run applications on system boot as well as restart applications in the event of an exception that causes the application to stop unexpectedly.  The following guide outlines the installation of PM2 on a Linux server and explains its basic use.  <br><br><b><em>Note - npm (node package manager) installation is assumed for the use of this guide.  Ensure npm is installed on server prior to utilizing this guide.</b></em></p>

<h2>Installation</h2>
<p>It is typically a good idea to NOT use sudo when installing and working with pm2.</p>

```bash
# Install pm2 using npm.
npm install pm2@latest -g 
```

<p>With PM2 installed you can now start a node application using the process manager</p>


```bash
# Navigate to node app root directory.
cd /apps/express/test-app
```


```bash
# Use the following command to start the node application using PM2
# The --name flag is used to give the process a name.
# the --watch flag tells pm2 to restart the application when it detects a change in the codebase.
# Replace 'npm run start' with whatever script is used to launch the node application.
pm2 start 'npm run start' --name test-app --watch
```


```bash
# Save pm2 process list to ensure processes automatically start on system boot
pm2 save
```


```bash
# Check status of pm2 processes
pm2 status
```


<p>You should now have PM2 installed on server and managing a single application.  For further help with PM2 please visit the official documentation found <a href="https://pm2.keymetrics.io/docs/usage/quick-start/" target="_blank">here</a></p>
# librarymanagmentsysteminphp

Import library_managment.sql on database
1. Server Provisioning:

a. Choose a Cloud Provider and Provision a VPS:

Choose a cloud provider AWS and create a EC2 instance.
Note down the instance IP address, username, and password or SSH key.
b. Secure Linux Distribution and Firewall:

Log in to your Instance using SSH.
Update package lists: sudo apt update
Upgrade existing packages: sudo apt upgrade
Install Uncomplicated Firewall (UFW): sudo apt install ufw
Allow SSH: sudo ufw allow OpenSSH
Allow HTTP and HTTPS: sudo ufw allow 'Nginx Full'
Enable UFW: sudo ufw enable
c. Install LEMP Stack:

Install Nginx: sudo apt install nginx
Install MySQL/MariaDB: sudo apt install mysql-server
Run secure installation for MySQL: sudo mysql_secure_installation
Install PHP and required extensions: sudo apt install php-fpm php-mysql php-curl php-gd php-mbstring php-xml php-xmlrpc php-zip
2. Website Configuration:

a. WordPress Installation:

Navigate to Nginx web root: cd /var/www/html
Download WordPress: sudo wget https://wordpress.org/latest.tar.gz
Extract: sudo tar -xzvf latest.tar.gz
Rename: sudo mv wordpress your-site-name
Set ownership: sudo chown -R www-data:www-data your-site-name
b. Secure WordPress:

Create a new MySQL/MariaDB database and user for WordPress.
Edit WordPress configuration: sudo nano /var/www/html/your-site-name/wp-config.php

c. SSL/TLS Certificate:

Install Certbot: sudo apt install certbot python3-certbot-nginx
Obtain certificate: sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
d. Nginx Optimization:

Edit Nginx config: sudo nano /etc/nginx/nginx.conf
Implement caching and gzip compression.
Reload Nginx: sudo systemctl reload nginx
3. GitHub Repository Setup:

a. Create GitHub Repository:

Create a new repository on GitHub.
b. GitHub Actions Workflow:

Inside your repository, go to the "Actions" tab and create a new workflow.
Create .github/workflows/blank.yml.
c. Workflow Steps:

Define workflow name, triggers, and environment variables (e.g., SERVER_IP, SSH_PRIVATE_KEY).
Use SSH actions or SCP commands to securely transfer files to the server.
SSH into the server and run necessary commands (e.g., update, restart Nginx, etc.).

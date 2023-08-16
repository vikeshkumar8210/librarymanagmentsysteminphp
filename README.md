# librarymanagmentsysteminphp

Import library_managment.sql on database

# Server Provisioning:

1. Choose a Cloud Provider and Provision a VPS:

Choose a cloud provider AWS and create a EC2 instance.
Note down the instance IP address, username, and password or SSH key.
2. Secure Linux Distribution and Firewall:

Log in to your Instance using SSH.
Update package lists: sudo apt update
Upgrade existing packages: sudo apt upgrade
Install Uncomplicated Firewall (UFW): sudo apt install ufw
Allow SSH: sudo ufw allow OpenSSH
Allow HTTP and HTTPS: sudo ufw allow 'Nginx Full'
Enable UFW: sudo ufw enable
3. Install LEMP Stack:

Install Nginx: sudo apt install nginx
sudo systemctl start ngnix
sudo systemctl status ngnix
sudo systemctl enable ngnix
Install MySQL/MariaDB: sudo apt install mysql-server mysql-client
Run secure installation for MySQL: sudo mysql_secure_installation
sudo systemctl start mysql
sudo systemctl status mysql
sudo systemctl enable mysql
Install PHP and required extensions: sudo apt install php-fpm php-mysql php-curl php-gd php-mbstring php-xml php-xmlrpc php-zip
# Website Configuration:

1. WordPress Installation:

Navigate to Nginx web root: cd /var/www/html
Download WordPress: sudo wget https://wordpress.org/latest.tar.gz
Extract: sudo tar -xzvf latest.tar.gz
Rename: sudo mv wordpress your-site-name
Set ownership: sudo chown -R www-data:www-data your-site-name
2. Secure WordPress:

Create a new MySQL/MariaDB database and user for WordPress.
Edit WordPress configuration: sudo nano /var/www/html/your-site-name/wp-config.php

3. SSL/TLS Certificate:

Install Certbot: sudo apt install certbot python3-certbot-nginx
Obtain certificate: sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
4. Nginx Optimization:

Edit Nginx config: sudo nano /etc/nginx/nginx.conf
Implement caching and gzip compression.
Reload Nginx: sudo systemctl reload nginx
# GitHub Repository Setup:

1. Create GitHub Repository:

Create a new repository on GitHub.
2. GitHub Actions Workflow:

Inside my repository, go to the "Actions" tab and create a new workflow.
Create .github/workflows/blank.yml.
c. Workflow Steps:

Define workflow name, triggers, and environment variables (e.g., SERVER_IP, SSH_PRIVATE_KEY).
Use SSH actions or SCP commands to securely transfer files to the server.
SSH into the server and run necessary commands (e.g., update, restart Nginx, etc.).

# Documentation of project-2.

Launch an instance

Connect to your server through ssh

## installing Nginx 

`sudo apt update`

`sudo apt install nginx`

To Check the status: `sudo systemctl status nginx`

![nginx running](./images/nginx-running.PNG)

Open port 80

`http://<Public-IP-Address>:80`

![nginx image](./images/image1-project-2.png)

## Installing Mysql

`sudo apt install mysql-server`

`sudo mysql`

![mysql running](./images/mysql-install.PNG)

## Installing PHP

`sudo apt install php-fpm php-mysql`

## Configure Nginx to use PHP

Create the root web directory for your_domain

`sudo mkdir /var/www/projectLEMP`

Assign ownership of the directory with the $USER environment variable:`sudo chown -R $USER:$USER /var/www/projectLEMP`

Open a configuration file in Nginx: `sudo nano /etc/nginx/sites-available/projectLEMP`

![configuration code](./images/nano-nginx.PNG)

Activate configuration: `sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

`sudo nginx -t`

![configuration message](./images/configuration-message.PNG)

Disable default Nginx to listen to port 80: `sudo unlink /etc/nginx/sites-enabled/default`

Reload Nginx: `sudo systemctl reload nginx`

`sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

In your browser: [Browser](http://<Public-IP-Address>:80)

![message](./images/lemp-message.PNG)

Or [DNS](http://<Public-DNS-Name>:80)

## Testing PHP with NGINX

Create a PHP file: `sudo nano /var/www/projectLEMP/info.php`

Enter `<?php
phpinfo();`

[Browser](http://`server_domain_or_IP`/info.php)

![Zend engine](./images/Zend-engine.PNG)

Remove the file you created:`sudo rm /var/www/your_domain/info.php` 

## Retrieving data from Mysql database with PHP
`sudo mysql`

![error message](./images/error-message.PNG)

Had an error message and was able to rectify it with: `mysql -u root -p`, then type in your password.

Create a new database
`mysql> CREATE DATABASE `example_database`;`


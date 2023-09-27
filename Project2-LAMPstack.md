# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

# LAMP STACK 
### The LAMP stack is a popular and widely used software stack for building and deploying web applications. It's an acronym that stands for:
###    1. Linux: This refers to the operating system on which the web application will be hosted. Linux is chosen for its stability, security, and open-source nature.
###    2. Apache: Apache HTTP Server (commonly referred to as Apache) is a powerful and widely used web server software. It handles the serving of web pages, processing requests from users' browsers, and directing them to the appropriate files on the server.
###    3. MySQL: MySQL is a popular open-source relational database management system (RDBMS) that stores and manages the data for the web application. It's used for storing information such as user data, content, configurations, and more.
###    4. PHP: PHP stands for Hypertext Preprocessor. It's a scripting language that is often used for server-side programming to generate dynamic web content. PHP scripts are executed on the server and can interact with the database, handle user input, and generate HTML for web pages.

# Step 0 - Preparing prerequisites
## Connecting to an AWS ubuntu server.
![Screenshot from 2023-09-18 02-07-13](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/0b10c313-2bdb-40a2-8a07-2c726a8bb9c9)

## Changing permission for the private key file (.pem) and connecting to the AWS Ubuntu Server.
$ sudo chmod 0400 <private-key-name>.pem

$ ssh -i "ubuntu-server.pem" ubuntu@ec2-34-207-174-161.compute-1.amazonaws.com

![image](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/9af8b790-deaa-4d22-9372-eabb2d2f89aa)

# Step 1 - Installing Apache and Updating the Firewall
## To ensure functionality, update a list of packages in package manager
$ sudo apt update
![image](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/e78f72d9-2c26-472e-8129-c84b8b3ce637)

## run apache2 package installation
$ sudo apt install apache2
!![image](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/e69b3927-ec88-4cca-bd42-a937f6ef4184)

## To verify that apache2 is running as a Service in our OS, use following command
$ sudo systemctl status apache2
![image](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/502ae1ba-5cf4-4975-b0ce-1b66f810bc0b)

## Before we can receive any traffic by our Web Server, we need to open TCP port 80 which is the default port that web browsers use to access web pages on the Internet
![Screenshot from 2023-09-18 02-21-26](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/bd237cce-dda3-4c51-b88b-d4df906ac185)

## To confirm that our Apache HTTP server can be accessed locally in our Ubuntu shell, and can respond to requests from the Internet
### Accessing our server locally in our Ubuntu shell.
$ curl http://localhost:80
![Screenshot from 2023-09-18 02-23-30](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/135ddf7c-4137-431c-8562-62f5fba07830)

or
$ curl http://127.0.0.1:80
![Screenshot from 2023-09-18 02-25-06](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/1a3375e8-9ef5-4dfa-88d6-4439ee5cb914)

## To test how our Apache HTTP server can respond to requests from the Internet. Open a web browser of your choice and try to access following url.
$ http://<Public-IP-Address>:80
##or 
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
![Screenshot from 2023-09-18 02-29-22](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/b1a9f363-471f-4792-a0e9-07669cdf9b10)



# Step 2 - Installing Mysql
## To acquire and install Mysql software:
$ sudo apt install mysql-server
![Screenshot from 2023-09-20 22-15-46](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/c21a962a-07a1-44b5-bdcb-910bc9c38dee)

## To connect to the MySQL server as the administrative database user root
$ sudo mysql
![Screenshot from 2023-09-18 14-25-27](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/7c7e5cba-cccb-41e1-9adc-962f499a440b)

$ sudo mysql_secure_installation
![Screenshot from 2023-09-18 14-36-03](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/905cd558-78a9-48a8-9ce7-d19064279402)

![Screenshot from 2023-09-18 14-40-26](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/b69dd7fc-74d2-4d47-8806-7d11b92a7efc)

![Screenshot from 2023-09-18 14-43-50](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/2af99caf-4152-4498-812a-cdb03a929e30)

## To confirm if we are able to log into MySQL console.
$ sudo mysql -p
![Screenshot from 2023-09-18 14-46-12](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/67cd2d28-84e0-4b24-860f-0a4b4aff16ee)

$ mysql> exit
![Screenshot from 2023-09-18 14-48-18](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/b55d7a91-5792-4196-8ccb-19d6b65d0727)

### MySQL is confirmed to have been installed and ready to use.

# Step 3 - Installing PHP
## For PHP processes codes to display dynamic contents to the end user. It works with php-mysql; a PHP module that allows PHP to communicate with MySQL-based databases, libapache2-mod-php whcih enable Apache to handle PHP files and Core PHP packages which are automatically installed as dependencies.
### To install these 3 packages at once, run:
$ sudo apt install php libapache2-mod-php php-mysql
![Screenshot from 2023-09-18 14-59-36](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/d0f52524-5358-4ee7-9cb2-b6437f2ca634)

## To confirm the version of PHP installed.
$ php -v
![Screenshot from 2023-09-18 15-00-05](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/1804ba92-d4b4-4e44-9199-1bcb242e9b00)
## The LAMP stack is now fully installed and confirmed operational.


# Step 4 — Creating/configuring a Virtual Host for your Website using Apache
## To set up a domain called "projectlamp", Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory. We will leave this configuration as is and will add our own directory next to the default one.
### To create the directory for projectlamp using 'mkdir' command as follows:
$ sudo mkdir /var/www/projectlamp
![Screenshot from 2023-09-27 00-24-41](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/87d957c0-a603-494e-9657-00100cf99e37)

## Assign ownership of the directory with the $USER environment variable, which will reference your current system user:
$ sudo chown -R $USER:$USER /var/www/projectlamp
### Then, create and open a new configuration file in Apache’s sites-available directory using your preferred command-line editor. with the use of vim.
$ sudo vi /etc/apache2/sites-available/projectlamp.conf
![Screenshot from 2023-09-27 00-32-37](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/cc19a0bc-ef63-4b23-ad86-e8457b408879)

### This will create a new blank file. Paste in the following bare-bones configuration:
$ <VirtualHost *:80>

$    ServerName projectlamp

$    ServerAlias www.projectlamp 

$    ServerAdmin webmaster@localhost

$    DocumentRoot /var/www/projectlamp

$    ErrorLog ${APACHE_LOG_DIR}/error.log

$    CustomLog ${APACHE_LOG_DIR}/access.log combined

$ </VirtualHost>


![Screenshot from 2023-09-27 00-29-21](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/c6877dcf-0024-4a01-89e7-4b3fbd0c5e87)


## To show the new file in the sites-available directory.
$ sudo ls /etc/apache2/sites-available
![Screenshot from 2023-09-27 00-34-54](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/4f6601a4-89f8-4a6d-83cb-886233766117)


### With this VirtualHost configuration, we’re telling Apache to serve projectlamp using /var/www/projectlampl as its web root directory. 

## To enable the new virtual host using a2ensite command:
$ sudo a2ensite projectlamp


## To disable Apache’s default website use a2dissite command , type:
$ sudo a2dissite 000-default
![Screenshot from 2023-09-27 00-37-57](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/c30ab112-984b-4ea5-9df5-ca0ddac12301)

# To make sure your configuration file doesn’t contain syntax errors, run:
$ sudo apache2ctl configtest

# Finally, reloading Apache so these changes take effect:
$ sudo systemctl reload apache2
![Screenshot from 2023-09-27 00-44-30](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/7f5c28c5-bef9-4568-912c-9895c1023290)


## The new website is now active, with an empty web root /var/www/projectlamp.
### To create an index.html file in that location so that we can test that the virtual host works as expected:
$ sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
![Screenshot from 2023-09-27 00-44-30](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/575e99e1-e105-4aed-a883-3eb700344459)

## To open our new website URL using IP address through a browser.
$ http://<Public-IP-Address>:80
![Screenshot from 2023-09-27 00-49-56](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/49b44a84-f91f-44b4-87b4-dae55aefea2d)

## To open our new website URL using public DNS name through a browser.
$ http://<Public-DNS-Name>:80
![Screenshot from 2023-09-27 00-53-30](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/1b8ae080-81dc-4365-8ad3-0637878e7b8a)  


# Step 5 — Enable PHP on the website
## With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file. 
## To edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive and make it the default landing page for the application
## To edit the DrectoryIndex for index.php file to take precedence over the index.html file.
$ sudo vim /etc/apache2/mods-enabled/dir.conf
![Screenshot from 2023-09-25 22-34-57](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/ba339da6-3ed7-4dbf-80da-67eb68ea69a0)

## After saving and closing the file, you will need to reload Apache so the changes take effect:
$ sudo systemctl reload apache2
![Screenshot from 2023-09-25 22-37-55](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/39b2fe65-3564-4a38-bafa-883e856d585c)

## To create a PHP script to test that PHP is correctly installed and configured on your server.
$ sudo mkdir /var/www/projectlamp
![Screenshot from 2023-09-25 23-27-38](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/5a15d7fc-c6f4-4803-bd86-ab99ac73e09b)

## To open a blank file and add PHP code.
$ <?php
$ phpinfo();

$ vim /var/www/projectlamp/index.php
![Screenshot from 2023-09-21 22-42-57](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/75659beb-4a39-41ec-a430-549a1e12ba3c)

## TO confirm that the configuration is done, refresh the webpage after saving.
![Screenshot from 2023-09-27 01-02-39](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/295a2984-fb55-4655-912c-cb7215b235cf)

## After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment -and your Ubuntu server. Run the following command.
$ sudo rm /var/www/projectlamp/index.php
![Screenshot from 2023-09-25 23-46-08](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/7ea50472-9cd5-4b06-8793-e15b338586b7)

## This completes the project.


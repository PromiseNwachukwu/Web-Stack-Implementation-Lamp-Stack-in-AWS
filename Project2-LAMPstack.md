![Screenshot from 2023-09-27 01-02-39](https://github.com/PromiseNwachukwu/Web-Stack-Implementation-Lamp-Stack-in-AWS/assets/109115304/cb696fbb-b8c4-4bed-8423-0b372f18f36e)# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

## LAMP STACK 

## LAMP (Linux- Operating System, Apache- Web Sever, MySQL- Data base, PHP or Python, or Perl- ) 

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


# Step 3 - Installing PHP
## PHP processes codes to display dynamic contents to the end user. It works with php-mysql; a PHP module that allows PHP to communicate with MySQL-based databases, libapache2-mod-php whcih enable Apache to handle PHP files and Core PHP packages which are automatically installed as dependencies.
To install these 3 packages at once, run:
$ sudo apt install php libapache2-mod-php php-mysql
![Screenshot from 2023-09-18 14-59-36](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/d0f52524-5358-4ee7-9cb2-b6437f2ca634)

$ php -v
![Screenshot from 2023-09-18 15-00-05](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/1804ba92-d4b4-4e44-9199-1bcb242e9b00)
## The LAMP stack is now fully installed and confirmed operational.






# Step 4 — Creating a Virtual Host for your Website using Apache
In this project, you will set up a domain called projectlamp, but you can replace this with any domain of your choice.
Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory. We will leave this configuration as is and will add our own directory next next to the default one.
Create the directory for projectlamp using 'mkdir' command as follows:
$ sudo mkdir /var/www/projectlamp
![Screenshot from 2023-09-27 00-24-41](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/87d957c0-a603-494e-9657-00100cf99e37)

Assign ownership of the directory with the $USER environment variable, which will reference your current system user:
$ sudo chown -R $USER:$USER /var/www/projectlamp
Then, create and open a new configuration file in Apache’s sites-available directory using your preferred command-line editor. Here, we’ll be using vi or vim (They are the same by the way):
$ sudo vi /etc/apache2/sites-available/projectlamp.conf
This will create a new blank file. Paste in the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:
![Screenshot from 2023-09-27 00-32-37](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/cc19a0bc-ef63-4b23-ad86-e8457b408879)

1c3e-4425-8ba3-c9a582ab3580)
![Screenshot from 2023-09-27 00-29-21](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/c6877dcf-0024-4a01-89e7-4b3fbd0c5e87)

To save and close the file, simply follow the steps below:
    1. Hit the esc button on the keyboard 
    2. Type : 
    3. Type wq. w for write and q for quit 
    4. Hit ENTER to save the file 
You can use the ls command to show the new file in the sites-available directory
$ sudo ls /etc/apache2/sites-available
![Screenshot from 2023-09-27 00-34-54](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/4f6601a4-89f8-4a6d-83cb-886233766117)


With this VirtualHost configuration, we’re telling Apache to serve projectlamp using /var/www/projectlampl as its web root directory. If you would like to test Apache without a domain name, you can remove or comment out the options ServerName and ServerAlias by adding a # character in the beginning of each option’s lines. Adding the # character there will tell the program to skip processing the instructions on those lines.
You can now use a2ensite command to enable the new virtual host:
$ sudo a2ensite projectlamp


You might want to disable the default website that comes installed with Apache. This is required if you’re not using a custom domain name, because in this case Apache’s default configuration would overwrite your virtual host. To disable Apache’s default website use a2dissite command , type:
$ sudo a2dissite 000-default
![Screenshot from 2023-09-27 00-37-57](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/c30ab112-984b-4ea5-9df5-ca0ddac12301)

To make sure your configuration file doesn’t contain syntax errors, run:
$ sudo apache2ctl configtest
Finally, reload Apache so these changes take effect:
$ sudo systemctl reload apache2
Your new website is now active, but the web root /var/www/projectlamp is still empty. Create an index.html file in that location so that we can test that the virtual host works as expected:
$ sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
![Screenshot from 2023-09-27 00-44-30](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/575e99e1-e105-4aed-a883-3eb700344459)

Now go to your browser and try to open your website URL using IP address:
$ http://<Public-IP-Address>:80
![Screenshot from 2023-09-27 00-49-56](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/49b44a84-f91f-44b4-87b4-dae55aefea2d)

If you see the text from 'echo' command you wrote to index.html file, then it means your Apache virtual host is working as expected. In the output you will see your server's public hostname (DNS name) and public IP address. You can also access your website in your browser by public DNS name, not only by IP - try it out, the result must be the same (port is optional)
$ http://<Public-DNS-Name>:80
![Screenshot from 2023-09-27 00-53-30](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/1b8ae080-81dc-4365-8ad3-0637878e7b8a)  

You can leave this file in place as a temporary landing page for your application until you set up an index.php file to replace it. Once you do that, remember to remove or rename the index.html file from your document root, as it would take precedence over an index.php file by default.



# Step 5 — Enable PHP on the website

$ sudo vim /etc/apache2/mods-enabled/dir.conf
![Screenshot from 2023-09-25 22-37-55](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/a1f0a789-1242-41d9-a611-084cee798d0a)

## After saving and closing the file, you will need to reload Apache so the changes take effect:
$ sudo systemctl reload apache2
![Screenshot from 2023-09-25 23-27-38](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/81807ba4-c1e1-4c70-9a7a-ba942827a68b)

## To edit the DrectoryIndex for index.php file to take precedence over the index.html file.
$ sudo vim /etc/apache2/mods-enabled/dir.conf
![Screenshot from 2023-09-25 22-34-57](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/ba339da6-3ed7-4dbf-80da-67eb68ea69a0)

## After saving and closing the file, you will need to reload Apache so the changes take effect:
$ sudo systemctl reload apache2
![Screenshot from 2023-09-25 22-37-55](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/39b2fe65-3564-4a38-bafa-883e856d585c)

## To create a PHP script to test that PHP is correctly installed and configured on your server.
$ sudo mkdir /var/www/projectlamp
![Screenshot from 2023-09-25 23-27-38](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/5a15d7fc-c6f4-4803-bd86-ab99ac73e09b)


$ vim /var/www/projectlamp/index.php
![Screenshot from 2023-09-27 01-02-39](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/295a2984-fb55-4655-912c-cb7215b235cf)

$ sudo chown -R $USER:$USER /var/www/projectlamp
![Screenshot from 2023-09-26 00-25-08](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/1d6a54af-7d69-4252-81fc-69fc1e0dee6f)


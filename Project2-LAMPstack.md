# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

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

## Step 5 — Enable PHP on the website


$ sudo vim /etc/apache2/mods-enabled/dir.conf
![Screenshot from 2023-09-25 22-37-55](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/a1f0a789-1242-41d9-a611-084cee798d0a)

## After saving and closing the file, you will need to reload Apache so the changes take effect:
$ sudo systemctl reload apache2
![Screenshot from 2023-09-25 23-27-38](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/81807ba4-c1e1-4c70-9a7a-ba942827a68b)


$ sudo mkdir /var/www/projectlamp

$ sudo chown -R $USER:$USER /var/www/projectlamp


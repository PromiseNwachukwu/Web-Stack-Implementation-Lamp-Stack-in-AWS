# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

## LAMP STACK 

## LAMP (Linux- Operating System, Apache- Web Sever, MySQL- Data base, PHP or Python, or Perl- ) 

# Preparing prerequisites
## Connecting to an AWS ubuntu server.
![Screenshot from 2023-09-18 02-07-13](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/0b10c313-2bdb-40a2-8a07-2c726a8bb9c9)

## Changing permission for the private key file (.pem) and connecting to the AWS Ubuntu Server.
$ sudo chmod 0400 <private-key-name>.pem
&
$ ssh -i "ubuntu-server.pem" ubuntu@ec2-34-207-174-161.compute-1.amazonaws.com

![image](https://github.com/PromiseNwachukwu/DevOps-Projects-Darey.io/assets/109115304/9af8b790-deaa-4d22-9372-eabb2d2f89aa)

# Installing Apache and Updating the Firewall
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
$ curl http://localhost:80
or
$ curl http://127.0.0.1:80
![Screenshot from 2023-09-18 02-21-26](https://github.com/PromiseNwachukwu/my-portfolio1/assets/109115304/bd237cce-dda3-4c51-b88b-d4df906ac185)

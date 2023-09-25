# Connecting to an AWS ubuntu server.
## Changing permission for the private key file (.pem) and connecting to the AWS Ubuntu Server.
$ sudo chmod 0400 <private-key-name>.pem

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


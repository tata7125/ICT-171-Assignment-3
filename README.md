# ICT-171-Assignment-3

## Student Details 
**Name:** Troi Arbollente  
**Student ID:** 35526226  
**Website:** https://www.countryhopper.life/  
**Public IP:** 3.25.154.77  
**Domain From:** GoDaddy  
**Cloud Service Provider:** AWS EC2  
 
## Overview   

This project involves the deployment of a cloud-based travel blog using an Amazon EC2 instance. The website was first configured usig NGINX, followed by the installation of WordPress as the content management system. My blog website will showcase 5 different countries with recommemendations for each country such as places to visit, eat, and activities. 

The project demonstrates the ability to provision and manage cloud infrastructure, configure a web server environment, and deploy a dynamic website accessible over the internet. Additional configuration such as domain integration and security (SSL/TLS) was implemented to improve accessibility and security.  

Overall, this project showcases practical skills in cloud computing, server administration, and web application deployment. 


## EC2 Instance Setup  
**Cloud Service Provider:** Amazon Web Services  
**Instance Type:** t3.micro  
**OS:** Ubuntu 24.04  

## Security Group  
**Ports:** 22 SSH Access, 80 HTTP Access, 443 HTTPS Access  
**Protocols:** All TCP  
**Source:** All 0.0.0.0/0

## SSH Access  
To access my instance, I first opened my terminal and change the directory where my .pem key is located which is: 
```
cd Downloads
```
And access the instance using:
```
ssh -i ict171.pem ubuntu@3.25.154.77
```

## NGINX 
**Installing**  
In my terminal I entered the following code to install NGINX.  
```
sudo apt update
sudo  apt install nginx -y
```
**Running**  
```
sudo systemctl start nginx
sudo systemctl enable nginx
```
## Obtaining a DNS  
1. Logged in to GoDaddy
2. Bought a domain name
3. Went to My Products -> Domains -> Manage DNS
4. Added a new record:
   ```
   Type  Name  Value        TTL 
   A     @     3.25.154.77  600
   A    www    3.25.154.77  600
   ```

## Enable Cert Bot for HTTPS 
```
$ sudo snap install --classic certbot
$ sudo ln -s /snap/bin/certbot /usr/local/bin/certbot
$ sudo certbot --nginx
```

## Obtaining Let's Encrypt SSL Certificate  
Type these commands in order.  
```
sudo apt update
sudo apt install certbot python3-certbot-nginx -y
```
Made sure my nginx is running by entering this command  
```
sudo systemctl status nginx
```
Requested for the SSL Certificate by entering  
```
sudo certbot --nginx -d countryhopper.life -d www.countryhopper.life
```
Auto-renewal test  
```
sudo certbot renew --dry-run
```
## Installing Apache2 and Maria DB
Apache2 is needed to host WordPress websites, running PHP apps, serving HTML files.  
Maria DB is needed to store data for my website.

Enter these commands  
```
sudo apt install apache2
sudo apt install mariadb-server mariadb-client
```

Run  
```
sudo mysql_secure_installation
```
You will then be prompted with  
```
Enter current password for root (enter for none):
```






























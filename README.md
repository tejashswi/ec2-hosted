
# Hosting a Website on AWS EC2 with Route 53 and SSL  

## Steps to Deploy

### 1. Launch EC2 Instance  
- Go to AWS Console, then EC2, then Launch Instance  
- Choose **Ubuntu**  
- Create and Use key pair
- Use Putty
- Allow **HTTP (80)**, **HTTPS (443)**, and **SSH (22)**  
- Launch instance
## Launched EC2 Instance
![EC2 Instance](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-15%20215813.png?raw=true)


![Anoter instance page](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-15%20215835.png?raw=true)


### 2. Connect to EC2 (using PuTTY/SSH)  
- Download Putty.exe file and install it in your device.
- Go to connection.
- Go to SSH
- Go to Auth
- Choose key pair file you made while creating instance.
```bash

login as username: ubuntu
```

### 3. Install Apache  
```bash
sudo apt install apache2
```

Check in browser → `http://yourpublicip`
- An Apache page will be shown to your public ip.

- 
- ![apache page]([https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-15%20202950.png?raw=true)

```bash
cd /var/www/html
sudo rm index.html
sudo vi index.html
```
- Press I to insert your own html code.
- Write your own code.
- After writing all code , Press Ctrl+C and then write ":wq" and Press Enter.
-![ After writing](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-08%20191627%20-%20Copy.png?raw=true)

### 5. Map Domain with Route 53  
- Register your own domain name.
- Go to Route 53 on AWS, Click on Hosted Zones.
## Route 53 Hosted Zone


![ hosted zone](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-15%20215927.png?raw=true)


- You will get four NS name server.
## NS Name Servers
![NS Name servers](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-15%20215904.png?raw=true)
- Then update these name server in your domain.
## Domain Name adding Name server
![Nameservereditedondomain](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-15%20215946.png?raw=true)
- Create **A record**
- Set your domain, Enter your allotted Public IP and then Map it.
## Website before SSL certfication (Showing Not Secure)
![Webiste before SSL certification](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-08%20191600.png?raw=true)

### 6. Enable SSL (HTTPS) using Certbot  
```bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache
```
- Then it will ask an email.
- Then it will ask your domain name , So just write it.
- Then SSL certification will deployed to your domain name.
  Check in browser → `https://yourpublicip`

## Website after SSL certfication using https (Showing Connection is Secure)
![Webiste ater SSL certification](https://github.com/tejashswi/ec2-hosted/blob/main/Screenshot%202025-11-11%20183732.png?raw=true)

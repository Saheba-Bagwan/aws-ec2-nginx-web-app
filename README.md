# AWS EC2 Web Server Deployment with Nginx

## 📌 Project Overview

This project demonstrates how to deploy and host a static HTML/CSS website on an **AWS EC2 instance** using **Nginx**.

The application is hosted on an Ubuntu EC2 server and is accessible through the instance's public IP address.

---

## 🏗️ Architecture

```text
                    Internet
                       │
                       ▼
                🌐 Web Browser
                       │
                       ▼
              Public IP of EC2
                       │
                       ▼
             🔐 AWS Security Group
                │              │
              SSH 22         HTTP 80
                │              │
                ▼              ▼
             Ubuntu EC2 Instance
                       │
                       ▼
                    Nginx
                       │
                       ▼
                 HTML / CSS
                       │
                       ▼
                  Web Page
☁️ AWS Services Used
Amazon EC2 – Hosts the web server
Amazon VPC – Provides the networking environment (default VPC)
Security Groups – Controls inbound network traffic
Amazon EBS – Provides persistent storage for the EC2 instance

IAM was studied as part of AWS access management, but it was not required to deploy this particular static website.

🛠️ Technologies Used
Ubuntu Linux
Nginx
HTML
CSS
SSH
Linux Terminal
AWS EC2
🚀 Implementation Steps
1. Launch EC2 Instance

Created an Ubuntu EC2 instance on AWS.

Configuration included:

Instance type: t3.micro
Ubuntu Server
EBS root volume
Default VPC
Key pair for SSH access
2. Configure Security Group

Configured inbound rules:

Protocol	Port	Source	Purpose
SSH	22	My IP	Remote server access
HTTP	80	0.0.0.0/0	Website access
3. Connect to EC2 Using SSH

Connected to the Ubuntu server using the EC2 key pair:

ssh -i simple-web-app-key.pem ubuntu@<EC2-PUBLIC-IP>
4. Update Ubuntu Packages
sudo apt update
5. Install Nginx
sudo apt install nginx -y
6. Verify Nginx
sudo systemctl status nginx

Nginx was successfully running.

7. Deploy Website

The custom website was placed in:

/var/www/html/index.html
8. Test Nginx Locally
curl -I http://localhost

Response:

HTTP/1.1 200 OK
9. Test Through Public IP

The website was also tested from the local computer:

curl -I http://<EC2-PUBLIC-IP>

Response:

HTTP/1.1 200 OK
🔍 Verification

Nginx service:

sudo systemctl is-active nginx

Output:

active

HTTP response:

HTTP/1.1 200 OK
Server: nginx
Content-Type: text/html

This confirms that the web server was successfully configured and the website was reachable through the EC2 public IP.

📚 What I Learned

Through this project, I practiced:

Launching and configuring an AWS EC2 instance
Working with Ubuntu Linux
Configuring AWS Security Groups
Connecting to a cloud server using SSH
Installing and managing Nginx
Hosting a static website
Understanding public and private IP addresses
Basic AWS networking
Using Linux commands
Testing HTTP services using curl
Troubleshooting SSH connectivity
Deploying files from a local machine to an EC2 server using scp
🎯 Project Outcome

Successfully deployed a static HTML/CSS website on an AWS EC2 Ubuntu server using Nginx and made it accessible over the internet through the EC2 public IP.

👩‍💻 Author

Saheba Bagwan

GitHub: Saheba-Bagwan

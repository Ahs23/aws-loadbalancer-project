✅ README.md (AWS Load Balancer Project — Enhanced & Professional)
AWS Load Balancer Project

A practical hands-on project demonstrating how to deploy a scalable, fault-tolerant web application on AWS using:

EC2 Instances

Application Load Balancer

Target Groups

Security Groups

User Data (Bootstrap Script)

Auto Health Checks

Cross-Zone Load Balancing

This project proves the ability to design and deploy a high-availability production-style architecture.

🔧 Project Architecture
           ┌──────────────────────────┐
           │   Internet Users         │
           └──────────────┬───────────┘
                          ▼
              ┌───────────────────────┐
              │ Application Load       │
              │      Balancer          │
              └──────────────┬────────┘
                             ▼
            ┌────────────────────────────────┐
            │      Target Group (HTTP:80)    │
            └──────────────┬─────────────────┘
                           ▼
        ┌───────────────────────────┬───────────────────────────┐
        ▼                           ▼                           ▼
  EC2 Instance 1            EC2 Instance 2          (Auto Scale Optional)
  User-data HTML App        User-data HTML App      Future Enhancement

✨ Project Features
✔️ Load Balancer Distributes Traffic

When the user refreshes the browser, the Load Balancer alternates between Server 1 and Server 2, displaying different content.

✔️ Custom Web Page via User Data

Each EC2 instance automatically deploys a web page on startup:

Server 1 → Blue Page

Server 2 → Green Page

This visually proves load balancing works.

✔️ Health Checks Automatically Monitor EC2 Instances

If any server is:

Stopped

Unhealthy

Fails HTTP response

…the Load Balancer automatically removes it from rotation.

✔️ Security Group Rules for Safe Access

ALB → Allows HTTP (80) from the internet

EC2 → Allows HTTP only from Load Balancer security group

✔️ Publicly Accessible Application

Your Load Balancer DNS name exposes the app globally.

📂 Project Files Included

✔ LoadBalancer.jpg
✔ TargetGroup.jpg
✔ UserData Script for Server 1.jpg
✔ UserData Script for Server 2.jpg
✔ Security-Group.jpg
✔ Functionality demo video

🚀 Technologies Used
Service	Purpose
EC2	Hosts the web servers
Application Load Balancer	Distributes traffic
Target Group	Tracks the registered instances
Security Groups	Controls inbound/outbound access
User Data	Automates deployment of HTML
IAM	Allows access to EC2 & Load Balancer services
VPC	Networking foundation (subnets, routing)
🧪 How to Reproduce This Project
1️⃣ Launch Two EC2 Instances

Amazon Linux 2

t2.micro (free tier)

Add user data:

Server 1 (HTML Blue Page)
#!/bin/bash
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Server 1 – Blue Page</h1>" > /var/www/html/index.html

Server 2 (HTML Green Page)
#!/bin/bash
#!/bin/bash
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Server 2 – Green Page</h1>" > /var/www/html/index.html

2️⃣ Create a Target Group

Target type: Instance

Protocol: HTTP

Port: 80

Health check path: /

Register both EC2 instances.

3️⃣ Create an Application Load Balancer

Internet-facing

Add listener: HTTP 80

Attach your Target Group

4️⃣ Test

Open:

http://<your-load-balancer-dns-name>


Refresh → You’ll see alternating responses:

Server 1 page

Server 2 page

🎉 Your Load Balancer works!

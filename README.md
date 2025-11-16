## 🚀 Networking Project — EC2, NGINX & Cloudflare DNS

This project is part of my DevOps learning journey, where I deployed a fully working public web server on AWS EC2, installed NGINX, configured networking and firewall rules, and connected a custom domain through Cloudflare DNS.

More than just spinning up a server, this project helped me understand how the internet truly works — from IP addressing and ports to DNS routing and cloud infrastructure.

⭐ Project Motivation
---
I wanted to truly understand how real traffic flows across the internet — not just in theory but in practice.

Networking is one of the most important foundations for DevOps, and this project helped me see:

how cloud servers receive requests

how DNS maps a domain name to an IP

how firewalls allow or block traffic

how NGINX serves content

how everything ties together end to end

This is the kind of hands-on experience that builds confidence and real skills.

📘 Project Summary
---
Here’s what I accomplished:

Launched an Amazon Linux 2023 EC2 instance

Connected via SSH using a secured .pem file

Installed and ran the NGINX web server

Configured Security Groups to allow HTTP (80) + SSH (22)

Purchased my domain through Cloudflare

Added an A Record pointing domain → EC2 Public IP

Successfully accessed NGINX through:

EC2 Public IPv4: 18.224.58.2

My domain: paramjyot2ray.com

By the end, everything worked seamlessly — and I finally understood the full networking flow.

🛠️ Technologies Used
--
AWS EC2 (Amazon Linux 2023)

NGINX Web Server

Cloudflare DNS

Linux (WSL)

SSH Key Authentication

AWS Security Groups

Systemd (systemctl)

🧩 1. Launching EC2 & SSH Access
--
🔐 Key Pair Setup

I created a key pair named Networking (2).pem, moved it into WSL, and secured its permissions:

cp /mnt/c/Users/Param/Downloads/Networking\ \(2\).pem ~/
chmod 400 "Networking (2).pem"

💻 SSH Into EC2
ssh -i "Networking (2).pem" ec2-user@18.224.58.2


Once authenticated, I had full access to my Linux server.

🌐 2. Installing & Running NGINX
--

Install NGINX:

sudo dnf install nginx -y


Start the server:


sudo systemctl start nginx


Verify it’s running:


sudo systemctl status nginx


Then test in a browser:

http://18.224.58.2


The default NGINX Welcome Page confirmed the web server was live.
--

🌍 3. Cloudflare DNS — Connecting My Domain

Inside Cloudflare, I added this DNS entry:

Type	Name	IPv4 Address	TTL	Proxy
A	@	18.224.58.2	Auto	OFF

Then visited:

http://paramjyot2ray.com


which loaded the same NGINX page — verifying DNS → EC2 routing works correctly.

💡 What I Learned
--
This project gave me practical experience with:

How DNS converts a domain into an IP

How cloud instances expose services across the internet

What ports, protocols, and firewalls do

Public vs private IP addressing

Running and managing Linux services

Secure access using SSH key pairs

How Cloudflare integrates with AWS

These are core concepts used every day in DevOps, SRE, and Cloud Engineering.

🧗 Challenges & How I Overcame Them
--
🔸 1. Wrong key pair on first instance

My first EC2 instance used a key pair I didn’t download.
Solution: Launched a new instance with a new .pem file.

🔸 2. Port 80 missing

SSH worked, but the website didn’t load.
Solution: Added HTTP port 80 to the Security Group.

🔸 3. Cloudflare proxy issues

EC2 didn’t work behind the Cloudflare orange proxy.
Solution: Turned proxy off (grey cloud).

🔸 4. SSH permission errors

I received the "UNPROTECTED PRIVATE KEY FILE" error.
Solution: Applied the required permissions:

chmod 400 "Networking (2).pem"


Each issue taught me real troubleshooting skills.

🌐 Install & Run NGINX
--
sudo dnf install nginx -y
sudo systemctl start nginx
sudo systemctl status nginx

🔎 Test Web Server
--
To verify that the NGINX server was working correctly, I tested it in my browser using both:

✔ My EC2 Public IPv4 Address
http://18.224.58.2

✔ My Cloudflare Domain
http://paramjyot2ray.com


Both displayed the NGINX welcome page, confirming that:

NGINX was running

Port 80 was open

DNS was correctly configured

Traffic successfully routed from Cloudflare → EC2 → NGINX

</details>
🔗 Connect With Me

LinkedIn

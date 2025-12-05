AWS VPC Setup 
Task: Create a Basic AWS Network (VPC + Subnets + IGW + NAT)

This task is about building a simple network in AWS.
A VPC (Virtual Private Cloud) is your own private network inside AWS.

What I created

1 VPC
▸ This is the main network.

2 Public Subnets
▸ Used for EC2 instances that need internet access.
▸ These subnets automatically get public IPs.

2 Private Subnets
▸ Used for EC2 instances that should NOT be directly exposed to the internet.

Internet Gateway (IGW)
▸ This gives internet access to public subnets.

NAT Gateway
▸ This gives private subnets access to go out to the internet
(e.g., to download updates), but keeps them safe from outside.

How it works

Public subnets can be reached from the internet.

Private subnets cannot be reached directly.

NAT Gateway only allows outbound internet traffic (safe for backend servers).

Route tables decide which subnet gets internet access.

Why this design is useful

Public subnet → For web servers

Private subnet → For databases, backend apps

Internet Gateway → For incoming/outgoing public traffic

NAT Gateway → For secure private traffic

Deliverables you should take screenshots of

VPC page

Public & private subnets

Internet Gateway

NAT Gateway

Route tables

Subnet route table associations

This completes the basic AWS networking setup.


EC2 Static Website Hosting with Nginx
Task: Deploy a Static Website on EC2 Using Nginx

This task teaches how to launch a server on AWS EC2 and host a basic webpage using Nginx.

What I did

Created a Key Pair
▸ This is needed to SSH into the EC2 instance.

Created a Security Group

Allowed HTTP (port 80) so the website can be viewed by anyone

Allowed SSH (port 22) only from my IP for security

Launched an EC2 Instance

Amazon Linux AMI (free tier)

t2.micro (free tier)

Placed it in public subnet

Enabled Auto-assign Public IP

Added a User-Data script
▸ Installs Nginx automatically
▸ Replaces the default web page with a simple resume

Opened the website
▸ Typed the EC2 public IP in the browser
▸ Saw the static resume webpage

Why Nginx?

It is a lightweight and fast web server

Perfect for simple static websites (HTML, CSS)

Basic Hardening Done

SSH restricted to my IP

Only essential service (Nginx) running

Server updated using yum update

No root login used (Amazon uses ec2-user)

Optional Automation

I also added Terraform code to automate:

VPC

Security Group

Key Pair

EC2 instance

User-data deployment script

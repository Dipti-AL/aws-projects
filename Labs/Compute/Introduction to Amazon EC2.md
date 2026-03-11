<b>Introduction to Amazon EC2<b>
Overview

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides virtual servers in the cloud. It allows easy adjustment of computing power, making it simple for developers to build and scale applications.

# Lab: Working with Amazon EC2

## Overview
This lab covers key Amazon EC2 tasks, including launching, monitoring, and managing an EC2 instance. By the end of this lab, the following skills will be demonstrated:

## Topics Covered
- Launched a web server with **termination protection** enabled
- Monitored the EC2 instance
- Modified the **security group** to allow HTTP access
- Resized the Amazon EC2 instance to scale
- Tested **termination protection**
- Terminated the EC2 instance

<img width="1607" height="513" alt="image" src="https://github.com/user-attachments/assets/fb31fc01-b556-4696-8a5a-190c9e08f11a" />

# Lab: Amazon EC2 Basics

## Overview
In this lab, I explored the fundamentals of Amazon EC2 by launching and managing a cloud-based web server. I began by creating an EC2 instance with termination protection enabled to safeguard against accidental deletion. While setting it up, I selected the Amazon Linux 2023 AMI and a t3.micro instance type, providing the right balance of CPU and memory for this practice. I configured the instance within a dedicated VPC and created a security group tailored for the web server, ensuring controlled access and security. A User Data script was deployed to automatically install and start an Apache web server and generate a simple HTML page, allowing immediate verification of server functionality once HTTP access was enabled.

Monitoring the instance introduced me to AWS’s built-in tools. I used EC2 Status Checks and CloudWatch metrics to track system performance and confirm reliability. Realizing that the server was initially inaccessible via HTTP, I modified the security group rules to allow web traffic on port 80, which demonstrated how security groups act as firewalls in AWS. To understand scalability, I resized the instance, stopping it first, then upgrading it to a t3.small type and expanding the EBS root volume from 8 GiB to 10 GiB, which showed how compute and storage resources can be adjusted to match workload needs. Finally, I tested termination protection by attempting to delete the instance, confirmed it was protected, and then disabled protection to safely terminate it.  

This hands-on experience provided a complete cycle of launching, configuring, securing, monitoring, scaling, and managing an EC2 instance, deepening my understanding of cloud infrastructure and best practices for maintaining reliable and secure applications in AWS.

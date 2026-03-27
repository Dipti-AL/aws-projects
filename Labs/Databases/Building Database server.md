**Lab 160 – Building a Database Server and Connecting via Web Application**

Overview

In this lab, I built a database backend using Amazon RDS and connected it to a web application running on EC2. The setup mimics a basic real-world architecture where an application interacts with a managed database service.

![Error Log](lab160_images/step_6.png)



Step 1: Create Security Group for RDS

I created a security group to allow MySQL access from the EC2 instance.

![Architecture](lab160_images/step_1.png)

Set up inbound rules:

![RDS Security Group](lab160_images/step_2.png)


Step 2: Create DB Subnet Group

For Subnets, For the first Availability zone, select 10.0.1.0/24, 
For the second Availability zone, select 10.0.3.0/24

Configured subnets in two availability zones:


![DB Subnet Group](lab160_images/step_3.png)

![DB Subnet Group](lab160_images/step_4.png)


Step 3: Launch RDS MySQL Instance

Engine: MySQL
Multi-AZ enabled
Dev/Test template

I will now configure and launch a Multi-AZ Amazon RDS for MySQL database instance.
Full configuration – MySQL engine, Mutli AZ DB instance using Dev/Test template
Storage – General purpose SSD, choose Lap VPC, DB security group
Click on create database


![RDS Configuration](lab160_images/step_5.png)


Endpoint used:

lab-db.cdsdrdekqio5.us-west-2.rds.amazonaws.com



Step 5: Connect Web Application

Accessed application:

http://34.216.65.28/rds.php


![Application](lab160_images/step_7.png)

Click on RDS and interact with the database:


![Solution](lab160_images/step_8.png)

Issue Faced

Connection failed with:

Unable to establish connection

Checked logs:

sudo tail -f /var/log/httpd/error_log

Error:

mysqli_connect(): caching_sha2_password


Root Cause

MySQL 8 uses caching_sha2_password, but the PHP client does not support it.

Solution

Connected to RDS and updated authentication:

ALTER USER 'main'@'%' IDENTIFIED WITH mysql_native_password BY 'lab-password';
FLUSH PRIVILEGES;

Restarted Apache:

sudo systemctl restart httpd

Fixed the issue and connected to RDS from Application

![Connected to RDS from Application](lab160_images/step_9.png)


**Key Learnings**

Multi-AZ improves availability but needs correct subnet setup
Security groups must be tightly controlled
Authentication mismatches can break connectivity
Logs are critical for debugging

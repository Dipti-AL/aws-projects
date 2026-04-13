# Lab 267 – Build My Own VPC and Launch a Web Server

In this lab, I created a custom VPC, configured subnets, routing, security groups, and deployed an EC2 instance running a web server inside the VPC.

I started by creating a VPC using **VPC and More**, selecting 1 Availability Zone, 1 public subnet, and 1 private subnet. I renamed the resources as LabVPC, along with public and private subnets and their associated route tables.

![VPC Creation](lab267_images/1.png)

The VPC workflow was created successfully.

![VPC Workflow](lab267_images/2.png)

Next, I created additional subnets inside LabVPC. I created a second public subnet named Public Subnet 2 with CIDR 10.0.2.0/24 and a second private subnet named Private Subnet 2 with CIDR 10.0.3.0/24. Both subnets were created in no specific availability zone.

![Subnets Created](lab267_images/3.png)

After creating the subnets, I associated them with the appropriate route tables. I filtered resources for LabVPC, edited subnet associations, and ensured Public Subnet 2 was associated correctly with the public route table.

![Subnet Association](lab267_images/4.png)

After updating associations, the VPC now had properly configured public and private subnets across the environment.

![Route Table Updated](lab267_images/5.png)

Next, I created a security group for the web server to control inbound traffic.

![Security Group](lab267_images/6.png)

After that, I launched an EC2 instance to host a web server. I named it Web Server 1 and selected Amazon Linux 2 as the AMI with instance type t3.micro. I placed the instance inside LabVPC under Public Subnet 2, enabled auto-assign public IP, and attached the Web Security Group. I also used a user data script to install Apache, PHP, and download the web application.

```bash
#!/bin/bash
yum install -y httpd mysql php
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
chkconfig httpd on
service httpd start

```

After the instance launched successfully, I tried accessing the web application using the public DNS, but the page was not reachable and showed a connection refused error.

To troubleshoot, I checked the security group and found that SSH inbound rules were missing, so I added port 22 access. After that, I connected to the instance and checked Apache status, but the service was not running. The issue was caused by the user data script failing due to the mysql package, which is deprecated on Amazon Linux 2 and causes installation failure, preventing Apache from being installed.

To fix this, I manually installed the required packages and started Apache:

```bash
sudo yum install -y httpd php unzip
sudo systemctl start httpd
sudo systemctl enable httpd
```

Then I downloaded the application files manually into /var/www/html, extracted them, and restarted Apache:

```bash
cd /var/www/html
sudo wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
sudo unzip lab-app.zip
sudo systemctl restart httpd
```

After this, the web server started working successfully and I was able to access the application using the EC2 public DNS.

Alternatively, I noted that the correct approach is to fix the user data script by removing mysql and using only httpd, php, and unzip, ensuring Apache installs correctly during launch:

```bash
#!/bin/bash
yum update -y
yum install -y httpd php unzip
systemctl start httpd
systemctl enable httpd
cd /var/www/html
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip
```



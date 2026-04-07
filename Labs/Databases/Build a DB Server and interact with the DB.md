# Lab 162: My Journey Building an RDS Server and Connecting via EC2

I just finished a challenge lab where I had to set up an Amazon RDS database from scratch and get it talking to a Linux server. It was a great exercise in networking, security, and a bit of unexpected troubleshooting with Docker.

---

## Step 1: Provisioning the RDS Instance
First, I had to launch the database using either **Amazon Aurora** or **MySQL**. I went with a **MySQL engine**. There were some specific lab restrictions I had to follow to keep things within the free tier:

* **Template**: I chose the **Dev/Test** or **Free tier**.
* **Instance Class**: I used a burstable **db.t3** instance.
* **Storage**: I set it to **100 GB** using **General Purpose SSD (gp2)**.
* **Networking**: I made sure it was launched inside the **Lab VPC**.
* **Monitoring**: I disabled **Enhanced Monitoring** in the settings.

![1.png]

I made sure to save my credentials like the endpoint, username (`admin`), and password (`lab-password`) since I'd need those to log in later.

---

## Step 2: Fixing the Security Group
The database was up, but it was locked down. I had to go into the **Security Group** and add a new inbound rule so my Linux server could actually talk to the RDS instance.

* **Type**: MySQL/Aurora.
* **Protocol**: TCP.
* **Port**: 3306.
* **Source**: I set the rule to allow the database to be accessed.

![2.png]

---

## Step 3: Dealing with the "Authentication Plugin" Error
This is where it got tricky. I logged into my Linux server via Putty and installed the default MySQL client. However, when I tried to connect, I got a nasty error: `ERROR 2059 (HY000): Authentication plugin 'caching_sha2_password' cannot be loaded`.

**The Problem**: The MySQL client on the EC2 was too old to support the new authentication used by MySQL 8.
**The Solution**: Instead of messing with broken libraries on the server, I used **Docker** to run a modern MySQL 8 client.

**The commands I used:**
```bash
sudo yum install -y docker
sudo service docker start
sudo usermod -a -G docker ec2-user
# I logged out and back in here to apply the group change
sudo docker run -it --rm mysql:8 mysql -h [my-rds-endpoint] -u admin -p

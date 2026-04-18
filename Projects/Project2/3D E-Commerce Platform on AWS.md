# 3D E-Commerce Platform on AWS

## Project Overview

This project focuses on designing a cloud architecture for a 3D e-commerce platform using AWS services. The goal is to allow users to interact with products in 3D (rotate, zoom, visualize fit) before making a purchase.

The platform is designed to handle a large number of global users while maintaining high availability, scalability, performance, security, and cost efficiency.

---

## Requirements

The architecture was designed based on the following requirements:

- High Availability  
- Scalability  
- Performance  
- Security  
- Cost Optimization  

---

## Architecture Approach

The solution uses a dual-region deployment:

- Primary Region: Ireland (eu-west-1)  
- Secondary Region: Frankfurt (eu-central-1)  

This setup helps with disaster recovery, reduces latency for European users, and improves overall system reliability.

---

## Architecture Diagram

![Architecture Diagram](architecture.png)

> Note: Replace `architecture.png` with the actual path of your uploaded diagram in the repository.

---

## Services Used and Design Decisions

### Route 53
Used for DNS and traffic routing. Configured with failover and latency-based routing to direct users to the nearest healthy region.

### CloudFront
Acts as a CDN to deliver static content like 3D models and images from edge locations, reducing latency and improving load times.

### Amazon S3
Stores static assets such as images and 3D models. Cross-region replication ensures data is available in both regions.

### Application Load Balancer (ALB)
Distributes incoming traffic across multiple EC2 instances, improving fault tolerance and availability.

### Amazon EC2 with Auto Scaling
Handles backend application processing. Auto Scaling ensures the system can handle traffic spikes and replaces failed instances automatically.

### Amazon RDS
- Primary database in Ireland  
- Read replica in Frankfurt  

Improves read performance and supports failover.

### DynamoDB Global Tables
Used for session and cart data. Provides near real-time replication across regions to maintain user state during failover.

### ElastiCache (Redis)
Used for caching frequently accessed data, reducing database load and improving response time.

### Security Services
- IAM for access control  
- KMS for encryption  
- WAF for protection against common web attacks  

### Monitoring and Logging
- CloudWatch for metrics and alerts  
- CloudTrail for auditing API activity  

---

## How the Architecture Meets Requirements

### High Availability
- Dual-region deployment  
- Route 53 failover routing  
- Multi-AZ infrastructure  
- Auto Scaling and Load Balancing  

The system continues to operate even if one region fails.

### Scalability
- EC2 Auto Scaling adjusts compute capacity  
- DynamoDB scales automatically  
- S3 provides virtually unlimited storage  

Each region scales independently based on demand.

### Performance
- CloudFront reduces latency using global edge locations  
- Latency-based routing sends users to the nearest region  
- Local database reads reduce cross-region delays  

### Security
- Separate VPCs in each region  
- Private subnets for backend services  
- Encryption using KMS  
- WAF for application protection  
- IAM roles with least privilege access  

### Cost Optimization
- Pay-as-you-go pricing model  
- Use of Free Tier where applicable  
- CloudFront reduces data transfer costs  
- DynamoDB used for variable workloads instead of always-on databases  

---

## Trade-offs and Challenges

- Dual-region architecture increases cost  
- Data replication introduces slight latency  
- More complex system to manage  
- Maintaining consistency across regions requires careful design  

---

## Future Improvements

- Introduce AWS Lambda and SNS for event-driven processing  
- Use ECS with Fargate for containerized workloads  
- Migrate from RDS to Aurora for better performance and availability  
- Use S3 Intelligent-Tiering for cost optimization  
- Strengthen GDPR and data residency controls  

---

## Key Learnings

- Designing highly available systems using multi-region architecture  
- Understanding trade-offs between cost, performance, and reliability  
- How different AWS services integrate in a real-world architecture  
- Importance of scalability and fault tolerance in modern applications  

---

KetoLife Café – Static Website on AWS
Authors

Dipti, Svetlana, Valerie, Zineb

**Project Overview**

This project demonstrates the design, development, and deployment of a static restaurant website using AWS services.
The website was created for KetoLife Café, a keto-focused restaurant concept based in Zurich, with the goal of improving customer experience and streamlining interactions such as viewing menus and contacting the restaurant.

The project also explores how cloud technologies can help small businesses transition to a more efficient digital model.

**Architecture Flow**

    The user accesses the website through a web browser
    
    The request is sent to the Amazon S3 static website endpoint
    
    S3 retrieves the requested files (HTML, CSS, images)
    
    The website is rendered in the user’s browser
    
    This architecture is serverless, meaning:
    
    No EC2 instances are required
    
    No backend server management is needed
    
    AWS handles availability and scalability automatically

**AWS Services Used**

    Amazon S3
    
    Static website hosting
    
    Storage for HTML, CSS, and images
    
    Public access configuration

**Deployment Steps**

    Created HTML and CSS files for the website
    
    Organized assets (images, styles)
    
    Created an S3 bucket
    
    Enabled static website hosting
    
    Uploaded all website files
    
    Configured bucket policy for public access
    
    Accessed the website via S3 endpoint

**Screenshots**

    (Add your screenshots here)
    
    ![Homepage](screenshots/homepage.png)
    ![Menu](screenshots/menu.png)
    ![S3 Setup](screenshots/s3.png)
**Future Enhancements**

    To make the application more dynamic and production-ready:

    **User Authentication**
    
    Amazon Cognito for login and sign-up
    
    **Backend Processing**
    
    AWS Lambda for handling orders and bookings
    
    **Database**
    
    Amazon DynamoDB for storing customer data
    
    **API Integration**

    API Gateway to connect frontend and backend

**Benefits of Using AWS**

    Scalability – easily handles increasing users
    
    High Availability – reliable hosting infrastructure
    
    Cost Efficiency – pay-as-you-go pricing
    
    Security – controlled access and permissions

**Key Learnings**

    Hosting static websites using Amazon S3
    
    Managing bucket policies and permissions
    
    Structuring a frontend project for deployment
    
    Understanding real-world cloud migration use cases

**Live Demo**

(Add your S3 or GitHub Pages link here)

**Project Structure**
    ketolife-cafe/
    │
    ├── index.html
    ├── style.css
    ├── images/
    ├── screenshots/
    └── README.md
    
**Conclusion**

This project demonstrates how a simple static website hosted on AWS can help a small business establish a digital presence and improve customer interaction. It also lays the foundation for future cloud-based enhancements such as authentication, backend processing, and database integration.


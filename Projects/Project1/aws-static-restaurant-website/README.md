
**Static Website on AWS**


**Creators**

**Group 5 - Dipti, Svetlana, Valerie, Zineb**


http://keto-life-restuarant.s3-website-us-west-2.amazonaws.com


**KetoLife Cafe**

<img src="images/hero.jpg" alt="Homepage" width="700">


**Project Overview**

    This project demonstrates the design, development, and deployment of a static restaurant website using AWS services. 
    
    The website was created for KetoLife Café, a keto-focused restaurant concept based in Zurich, with the goal of improving 
    customer experience. Also streamlining interactions such asviewing menus and contacting the restaurant.
    
    The project also explores how cloud technologies can help small businesses transition to a more efficient digital model.



**Architecture Flow**


<img src="images/architecture.png" alt="Project Architecture" width="800">

    1. The user accesses the website through a web browser. 
    
    2. The request is sent to the Amazon S3 static website endpoint.   
    
    3. S3 retrieves the requested files (HTML, CSS, images).  
    
    4. The website is rendered in the user’s browser.    
    
    5. This architecture is serverless, meaning:
    
        - No EC2 instances are required    
        
        - No backend server management is needed
        
        - AWS handles availability and scalability automatically
        

**Project Structure**

```text
    aws-static-restaurant/
            ├── index.html                 # Main landing page
            ├── style.css                  # Custom CSS styling
            ├── images/                    # Custom error page
            │   ├── hero.png
            │   ├── burger.jpg             # Images (.png/.jpg)   
            │   ├── pizza.jpg
            │   ├── pasta.jpg
            │   ├── curry.jpg
            │   ├── cauliflower.jpg
            │   ├── AboutUs.png            # UI captures for documentation
            │   ├── KetoMenu.png
            │   ├── KetoMenu.png
            │   └── ContactUs.png
            │   └── ContactUs2.png
            └── README.md                  # Project documentation
```


**AWS Components used**

    - Amazon S3
    
    - Static website hosting
    
    - Storage for HTML, CSS, and images
    
    - Public access configuration


**Deployment Steps**

    1. Created HTML and CSS files for the website
    
    2. Organized assets (images, styles)
    
    3. Created an S3 bucket
    
    4. Enabled static website hosting
    
    5. Uploaded all website files and images
    
    6. Configured bucket policy for public access
    
    7. Accessed the website via S3 endpoint



**Website Screenshots**


Website url: http://keto-life-restuarant.s3-website-us-west-2.amazonaws.com

A vibrant, welcoming landing page featuring fresh, gourmet ingredients and the modern KetoLife Café aesthetic.

<img src="images/hero.png" alt="Homepage" width="800">


This screen introduces our founding team of four  women - Dipti, Svetlana, Valerie, and Zineb.

It also shares our shared mission to blend global flavors with clean eating to create a truly international dining experience.


<img src="images/AboutUs.png" alt="About Us" width="800">


A beautifully curated gallery showcasing artisan dishes like cauliflower crust pizzas and nutrient-dense lettuce burgers.

Every meal is crafted with locally-sourced ingredients to ensure a delicious experience that nourishes both body and soul.


<img src="images/KetoMenu.png" alt="Keto Menu" width="800">


<img src="images/KetoMenu2.png" alt="Keto Menu" width="800">


A clean, accessible space for the community to easily find our Zurich location and check our daily opening hours.


<img src="images/ContactUs.png" alt="Contact Us" width="800">


The integrated feedback form and direct email link ensure seamless communication and high-quality support for our guests.


<img src="images/ContactUs2.png" alt="Contact Us" width="800">

    
**Future Enhancements**

    To make the application more dynamic and production-ready:

    1. User Authentication
    
        Amazon Cognito for login and sign-up
    
    2. Backend Processing
    
        AWS Lambda for handling orders and bookings
        
    3. Database
    
        Amazon DynamoDB for storing customer data
    
    4. API Integration

        API Gateway to connect frontend and backend


**Challenges faced**

    - Corrected mismatches where the code looked for .png but the file was actually .jpg.

    - Fixed broken links caused by using a capital "I" in the folder name instead of lowercase "images".

    - Moved all photos from the main directory into the correct "images" sub-folder so it can be referenced correctly 
    from index.html.
    

**Key Learnings**

    - Hosting static websites using Amazon S3
    
    - Managing bucket policies and permissions
    
    - Structuring a frontend project for deployment
    
    - Understanding real-world cloud migration use cases for simple static websites

    
**Conclusion**

This project demonstrates how a simple static website hosted on AWS can help a small business establish a digital presence and improve customer interaction. It also lays the foundation for future cloud-based enhancements such as authentication, backend processing, and database integration.


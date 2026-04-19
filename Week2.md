# Cloud Computing Learning Notes - Week 2

## Day 6: AWS - Amazon Web Services

### How to create AWS account:
- **UI (User Interface)**  
  - Access AWS via browser (AWS Management Console) 
- **CLI (Command Line Interface)**  
  - A tool to interact with AWS services using commands in terminal
- **SDK (Software Development Kit)**  
  - Collection of libraries and tools for programming languages (Java, Python)

### What are AWS Account Policies?
- AWS account policies are rules that define who can access what in AWS and what actions they can perform.
- They are written in json format.
- They are mainly part of IAM (Identity and Access Management).They control permissions and security in your AWS account.

**Types of AWS Policies**
1. Identity-Based Policies
Attached to users, groups, or roles
Define what actions they are allowed or denied

✅ Example:
Allow a user to create an S3 bucket but not delete it

2. Resource-Based Policies
Attached directly to a resource (like an S3 bucket)
Define who can access that resource

✅ Example:
Allow public access to an S3 bucket for website hosting

3. AWS Managed Policies
Predefined by AWS
Ready to use

✅ Example: AmazonS3ReadOnlyAccess

4. Customer Managed Policies
Created by you
Fully customizable

## How does a website go live?
A website goes live when its files (HTML, CSS, JavaScript) are hosted on a server that is connected to the internet and accessible through a public URL or domain name. Users can access the website via a browser using this URL.

## Types of Websites : 
**1. Static Website-**
  - Fixed content  
  - Built using HTML, CSS, JS  
  - No backend or database  
  - Fast and easy to host 
  
**2. Dyanamic Website-**
  - Content changes based on user interaction  
  - Uses backend technologies (e.g., Node.js, Java, Python)  
  - Connected to databases  
  - Example: login systems, dashboards

## Hosting a Static Website using AWS S3
Steps involved:
1. Create an S3 bucket (bucket name should be globally unique)
2. Upload website files (HTML, CSS, JS)
3. Enable **Static Website Hosting** in bucket settings
4. Set index document (e.g., `index.html`)
5. Update bucket permissions to allow public access
6. Access the website using the generated endpoint URL.

## Object URL vs Website Hosted URL
- **Object URL**  
  - Direct link to an individual file in S3  
  - Example: accessing a single image or HTML file  

- **Website Hosted URL**  
  - Endpoint provided by S3 static hosting  
  - Supports default index page and proper website navigation  
  - Used to access the complete website  
## NOTE
- By default, **public access to an S3 bucket is blocked** for security reasons  
- We must explicitly allow access to make the website publicly accessible


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

Steps to follow:
🚀 Part 2: Host on AWS S3 (step-by-step):

🔹 Step 1: Login to Amazon Web Services
Go to AWS Console
Search → S3

🔹 Step 2: Create Bucket
Click Create bucket
Enter: Bucket name → must be unique
Example: my-netflix-clone-123
Region → choose closest (Mumbai is good)

🔹 Step 3: Disable Block Public Access ⚠️
Uncheck:
✅ “Block all public access”
Confirm warning
👉 Required to make website public

🔹 Step 4: Create Bucket
Click Create bucket

🔹 Step 5: Upload Website Files
Open your bucket
Click Upload
Upload:
HTML file
CSS folder
Images / JS (everything)
👉 Important:
Upload entire folder contents, not just HTML

🔹 Step 6: Enable Static Website Hosting
Go to Properties tab
Scroll → Static website hosting
Enable it
Set:
Index document → index.html
Save

🔹 Step 7: Set Bucket Policy (public access)
- Policies are written in JSON format
Go to Permissions → Bucket Policy and paste:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::YOUR-BUCKET-NAME/*"]
    }
  ]
}
👉 Replace:
YOUR-BUCKET-NAME
🔹 Step 8: Access your website
Go to:
Properties → Static website hosting
Open the endpoint URL

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

----

## Day 7: AWS - Amazon Web Services Pricing and Storage classes

## AWS Pricing (Overview)
AWS follows a **pay-as-you-go** pricing model, which means:
- You only pay for the services you use  
- No upfront cost or long-term commitment (in most cases)

## Key Pricing Concepts

- **Pay-as-you-go**: Pay only for actual usage  
- **Free Tier**: Limited free usage for new users (12 months + some always free services)  
- **Reserved Instances**: Lower cost if you commit for 1 or 3 years  
- **On-Demand Pricing**: Pay per usage without commitment  
- **Spot Instances**: Very low cost, but can be interrupted  

## AWS Pricing Example (S3)
- Charged based on:
  - Storage (GB per month)
  - Data transfer
  - Requests (PUT, GET, etc.)

We can use the amazon calculator link to calculate the pricing:

*https://calculator.aws/#/createCalculator/S3*

Refer this doscumentation to understand the pricing in detail:
*https://aws.amazon.com/s3/pricing/*


## Amazon S3 Storage Classes (Detailed)

S3 provides different storage classes to optimize **cost, availability, and access patterns**.

### 1. S3 Standard
Frequent access with high performance and availability 
- Used for frequently accessed data  
- High availability and durability  
- Low latency and high throughput  
- Best for: websites, apps, frequently used data   

### 2. S3 Intelligent-Tiering
Automatically optimizes cost based on access pattern 
- Automatically moves data between tiers based on usage  
- No need to manage storage manually  
- Slight monitoring cost applied  

- Tiers include:
  - Frequent access  
  - Infrequent access  
  - Archive tiers  

### 3. S3 Standard-IA (Infrequent Access)
Rarely accessed data with quick retrieval but lower cost
- Lower storage cost than Standard  
- Retrieval cost is higher  
- Data is still quickly accessible  
- Minimum storage duration: 30 days  

### 4. S3 One Zone-IA
Low-cost storage in a single zone for non-critical data
- Data stored in only one Availability Zone  
- Cheaper than Standard-IA  
- Less fault tolerant  
- Minimum storage duration: 30 days  

### 5. S3 Glacier Instant Retrieval
Archive storage with immediate access
- Archive storage but with **instant access**  
- Lower cost than Standard-IA  
- Suitable for rarely accessed but still needed quickly  
Archive storage with immediate access  

### 6. S3 Glacier Flexible Retrieval
Low-cost archive with flexible retrieval time
- Very low-cost archival storage  
- Retrieval time: minutes to hours  

- Retrieval options:
  - Expedited (minutes)  
  - Standard (hours)  
  - Bulk (cheapest, longest time)  
  
### 7. S3 Glacier Deep Archive
Cheapest storage for long-term archival with slow retrieval
- Cheapest storage option  
- Retrieval time: 12 hours or more  
- Best for long-term backups  
- Minimum storage duration: 180 days  


| Storage Class              | Access Frequency     | Cost        | Retrieval Time     |
|---------------------------|---------------------|-------------|--------------------|
| S3 Standard               | Frequent            | High        | Instant            |
| Intelligent-Tiering       | Varies              | Optimized   | Instant            |
| Standard-IA               | Infrequent          | Medium      | Instant            |
| One Zone-IA               | Infrequent          | Lower       | Instant            |
| Glacier Instant           | Rare                | Lower       | Instant            |
| Glacier Flexible          | Very Rare           | Low         | Minutes–Hours      |
| Glacier Deep Archive      | Very Rare           | Lowest      | Hours              |

## Key Points to Remember
- All classes (except One Zone-IA) store data in multiple AZs  
- Glacier classes are used for **archival purposes**  
- Choosing the right class = **cost optimization**  
- Lifecycle policies can automatically move data between classes  

## Real-Life Examples
- **S3 Standard** → Hosting a live website  
- **Standard-IA** → Old project files  
- **Glacier** → Backup data, logs, compliance storage

-----

# Day 8: AWS S3 Lifecycle Policies & Versioning

## What are Lifecycle Policies?

Lifecycle policies in S3 help **automate the management of objects** by defining rules to:
- Move objects between storage classes  
- Delete or manage objects after a certain time  
- It Helps in **cost optimization and efficient data management**

## Why use Lifecycle Policies?
- Reduce storage cost  
- Automatically archive old data  
- Delete unused or temporary files  
- Avoid manual management  

## Lifecycle Policy Actions

### 1. Transition Actions
- Move objects to a cheaper storage class after a specific time  
**Example:**
- After 30 days → move to Standard-IA  
- After 90 days → move to Glacier  

### 2. Expiration Actions
- Automatically delete objects after a defined period  
**Example:**
- Delete logs after 180 days  

## Lifecycle Policy Example (Flow)
- Day 0 → Upload file (S3 Standard)  
- Day 30 → Move to Standard-IA  
- Day 90 → Move to Glacier  
- Day 180 → Delete  
This gives a fully automated lifecycle

## NOTE:
- AWS policies can be updated anytime  
- But **Deny always overrides Allow**  

  If access is denied:
- Check if any Deny rule exists  
- Remove Deny to allow access  
So Final Rule:
Deny > Allow > Default Deny


## What is S3 Versioning?
Versioning allows you to **keep multiple versions of the same object** in a bucket.
- If a file is updated or deleted, older versions are still stored

## Why is Versioning Important?
- Protects against **accidental deletion**
- Helps recover **previous file versions**
- Maintains **history of changes**
- Useful for **backup and auditing**

## How Versioning Works
- When versioning is enabled:
  - Every upload creates a **unique Version ID**
  - Updating a file does NOT overwrite it
  - Instead, a new version is created

**Example:** 
1.file.txt (v1) → upload again → file.txt (v2)
- Both versions exist in the bucket.
2. url --->> V1(version 1) + obj1 (v1+obj1 gives unique **id**) So,
   url + id --->> V2 + Obj2 

Note : The storage also gets modified 
 - 10gb + 1gb = 11 gb --> v1
   v1 + 1 gb = 21 gb --> v2

## Versioning States

### 1. Enabled
- Fully active  
- New versions are created  

### 2. Suspended
- Stops creating new versions  
- Old versions are still available

## Important Concepts

### 1. Version ID
- Unique identifier for each version of an object  
- Used to retrieve specific versions  

### 2. Delete Marker
- Created when you delete a file  
- Acts like a "soft delete"  
- Original file still exists in older versions  

### 3. Storage Impact
- Each version consumes storage  
- More versions = higher cost  
- Important for cost management

S3 Versioning ensures **data safety and recovery** by keeping multiple versions of files.  
It is essential for preventing data loss and should be used along with lifecycle policies for cost optimization.

## Versioning + Lifecycle Policies
Versioning works best with lifecycle rules:
**Example:**
- Keep latest version in S3 Standard  
- Move old versions to Glacier after 30 days  
- Delete versions after 180 days  
**This helps in:**
- Cost optimization  
- Automated cleanup


## Real-Time Examples
### 1. Accidental File Deletion
#### Scenario:
You delete an important file from S3

👉 What happens:
- S3 adds a **Delete Marker**
- File looks deleted

✅ Recovery:
- Remove delete marker → old file is restored

### 2. Updating Website Files
#### Scenario:
You update `index.html` for your website

👉 Without versioning:
- Old file is lost ❌

👉 With versioning:
- Old version is still available ✅
- You can rollback if something breaks

### 3. Data Backup & Recovery
#### Scenario:
Your application overwrites a file by mistake

👉 With versioning:
- Previous version is still available  
- No data loss  

### 4. Protection Against Human Errors
#### Scenario:
Someone deletes multiple files

👉 With versioning:
- All files can be restored  
- No permanent loss 


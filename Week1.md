# Cloud Computing Learning Notes - Week 1

## Day 1: Basics of Computing

### A) What is Computing?
- Computing refers to the process of using computers to perform tasks such as calculations, data processing, and many similar  
- **Example:** Using a calculator app on a computer to solve mathematical problems.

**Data Input**->**Processing Data**->**Required Output**

Eg. We run a query on db, server processes the query and displays the output of query.

-Input: Keyboard, Mouse

-Process: cpu (varies acc. to device)

-Output: Monitor or display

### B) What is ROM?
- ROM (Read-Only Memory) is non-volatile memory that stores permanent instructions for the computer.  
- **Example:** The BIOS stored in ROM helps start the computer when powered on.

### C) What is RAM?
- RAM (Random Access Memory) is volatile memory used to temporarily store data and instructions while the computer is running.  
- **Example:** Opening multiple browser tabs uses RAM to keep them active.

### D) What is OS?
- An Operating System (OS) is software that manages computer hardware and software resources, providing services for applications.  
- **Example:** Windows, Linux, macOS and Andriod

>>**Functions Of OS**

a. process management

b. memory allocation

c. Device Management

d.File Management

### Why Netflix Switched to AWS
After major failure in service providation Netflix migrated to AWS, earlier it has used its own datacenters

- Scalability: Handles Millions of users

- Reliability : Avoid downtime

- Availability : Application got available world wide with ease

- Cost effciency : Pay for used service

---

## Day 2: Introduction to Cloud Computing

### A) What is Cloud Computing?
- Cloud computing means delivering computing services (like storage, servers, databases, networking, and software) over the internet.  
- **Example:** Google Drive allows you to store files online and access them anywhere.

#### Pillars of Cloud Computing:
1. Storage  
2. Server  
3. Database  
4. Networking  
5. Software  

### B) Why Use Cloud Computing?
- It reduces costs, increases flexibility, and allows access from anywhere without needing physical infrastructure.

### C) What is CSP?
- CSP (Cloud Service Provider) is a company that offers cloud services.  
- **Example:** Amazon Web Services (AWS), Microsoft Azure, Google Cloud.

### D) Key Benefits of Cloud Computing:
1. On-demand self-service  
2. Broad network access  
3. Resource pooling  
4. Rapid elasticity  
5. Measured service  

---

## Day 3: Pillars of Cloud Computing

Explain each pillar in a single line with example:

1. **Security** – Protects data and applications from threats.  
   *Example:* AWS Identity and Access Management (IAM).  

2. **Cost Optimization** – Efficiently manages expenses.  
   *Example:* Using auto-scaling to reduce unused resources. Follows 'pay-as-you-go' model 

3. **Reliability** – Ensures systems run consistently.  
   *Example:* Redundant servers in Google Cloud. 

4. **Performance Efficiency** – Optimizes resources for speed and responsiveness.  
   *Example:* Content Delivery Networks (CDNs) for faster website access.  

5. **Sustainability** – Minimizes environmental impact.  
   *Example:* Microsoft Azure using renewable energy for data centers.  

6. **Scalability & Flexibility** – Expands or reduces resources as needed.  
   *Example:* Scaling up servers during peak traffic.  

7. **Operational Excellence** – Improves processes and monitoring.  
   *Example:* Automated monitoring tools in AWS CloudWatch.  

---

## Day 4: AWS Global Infrastructure
### Components:
A) Region:
AWS has data centres in various places, named as Regions.
eg. US East (N. Virginia), Asia Pacific (Mumbai) 
- Each region contains many available zones (AZ). AZs are isolated data centres connected with high internet speed, which may conatin 60k-80k servers.

B) Edge Locations:
These are speacalized data centres, where AWS services being used in more amount. These are designed to cache data via Amazon CloudFront and reduce latency for end users.

Key feautures and Benefits:
- **Reduced Latency** : Data travels from neaby edge location resulting in reduced travel time as a result low latency as result application running with fast speed.
- **Enchanced Performance** : benificial while browsing data, streaming media resulting in good user experience.
- **Content caching** : Stores cached data of videos,photos and website content, primarly used by Amazon cloudFront.

Key use cases: **Amazon CloudFront**, **Lambda@Edge**, **Amazon Route 53**
1. Amazon CloudFront : Delivers data to user with low latency
2. Lambda@Edge : xecutes Lambda functions at edge locations to customize content, acting closer to the user.
3. Amazon Route 53 :  Uses edge locations to improve the speed and responsiveness of DNS queries

c) AWS Global Network: 
- AWS has global fiber network connecting Regions,AZs and edge locations. As result, faster data transfer, low latency and better user experience.

D) Data Centers:
- AWS data centers are secure, physical facilities that house critical IT infrastructure—servers, storage, and networking equipment—supporting cloud services.

---

## Day 5: Cloud Storage and Service Models
**Cloud Storage** - Storing data in cloud storage instead of local hard drive and accessing it via internet.

Key feautures and Benefits:
1. Accessiblity : One can access data from anywhere stored on cloud storage via internet connection.
2. Scalability and elasticity: One can increase/decrease the storage capacity as required
3. Cost Efffective: Pay as you use, pay for the used services
4. Security and backup: Providers often handle encryption, data redundancy, and automatic backups, protecting against data loss from hardware failure.

**Cloud Service Model** - IaaS, PaaS, and SaaS—define how computing resources are delivered over the internet, ranging from raw infrastructure to ready-to-use software.

1. Iaas -  Infrastructure as a Service 
Provided computing resources like VMs, storage and network on demands. Users mostly manages OS, applications and Data.
*eg:* Amazon EC2

2. Paas - Platform as a service
Provided OS, Servers, offers hardware & software tools often needed for app. development. Users manages application and data.
*eg:* Google App Engine.

3. Saas - Software as a service
Service provider manages everything, user only uses the provided software.
*eg:* - Google Workspace

**Cloud Layers** :

Networking → Storage → Servers → Virtualization → OS → Middleware → Runtime → Data → Application

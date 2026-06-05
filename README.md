# Aws-Static-Website-Hosting
Hosting a Static Website on AWS using S3, Route 53, ACM & Cloudfront


### Project Overview

This project demonstrates the deployment of a secure and globally distributed static website using AWS cloud services. 

The project focused on cloud infrastructure deployment and AWS service integration using a prebuilt static website template.

### The Architecture Integrates:

Amazon S3 for static website hosting Amazon Route 53 for DNS management AWS Certificate Manager (ACM) for SSL/TLS certificates Amazon CloudFront for global content delivery and HTTPS

The project was built as a hands-on cloud engineering and DevOps learning implementation to understand real-world AWS deployment workflows.


### Project Architecture

User ↓ Route 53 (DNS) ↓ CloudFront (CDN + HTTPS) ↓


### Project Objectives

- Deploy a static website on AWS
- Configure a custom domain
- Enable HTTPS security using SSL/TLS
- Deliver website content globally using CDN
- Gain practical AWS cloud experience
- Troubleshoot real-world deployment issues


### AWS Services Used

- Amazon S3 ---> Static website hosting
- Amazon CloudFront ---> CDN and HTTPS delivery
- Amazon Route 53 ---> DNS management
- AWS Certificate Manager (ACM) ---> SSL certificate management


### Step-by-Step Implementation

#### Step 1: Prepare Website Files

- Downloaded a static website template
- Extracted the ZIP file
- Opened project folder in VS Code
- Reviewed the website file
- Prepared the static website files for AWS deployment
- Uploaded the template files to Amazon S3 for hosting
    
    ##### Command Used
    
    - code .


#### Step 2: Create and Configure S3 Bucket

- Created an S3 bucket: glorychidinmaotulu.online
- Uploaded website files to the bucket
- Ensured index.html existed in the root directory


#### Step 3: Enable Static Website Hosting

**Configuration**

- Enabled Static Website Hosting
- Set: Index document: index.html

##### Result

- Website became accessible using the S3 website endpoint URL.


#### Step 4: Configure Bucket Policy

To allow public access to website files, the following bucket policy was configured:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::glorychidinmaotulu.online/*"
    }
  ]
}


#### Step 5: Configure Route 53 Hosted Zone

- Created hosted zone in Route 53
- Migrated domain DNS management from Namecheap to Route 53

Nameservers Updated
ns-xxx.awsdns-xx.org
ns-xxx.awsdns-xx.com
ns-xxx.awsdns-xx.net
ns-xxx.awsdns-xx.co.uk

##### Result

AWS successfully became the authoritative DNS provider for the domain.


#### Step 6: Request SSL Certificate (ACM)

- Requested SSL certificate in ACM
- Validated domain ownership using DNS validation (CNAME record)

##### Result

Certificate status changed:

Pending Validation → Issued


#### Step 7 : Configure CloudFront Distribution

- Created CloudFront distribution
- Connected S3 bucket as origin
- Added custom domain:

##### glorychidinmaotulu.online

- Attached ACM SSL certificate
- Enabled HTTP → HTTPS redirection
- Configured default root object:

index.html

##### Result

CloudFront globally distributed website content securely over HTTPS.


#### Step 8 : Connect Domain to CloudFront

- Created Route 53 Alias A Record
- Pointed domain to CloudFront distribution

##### Result

Website became accessible via custom domain and HTTPS.


### Challenges Faced & Troubleshooting

#### 1. AccessDenied Error

<Error>
  <Code>AccessDenied</Code>
  <Message>Access Denied</Message>
</Error>

##### Cause
- Incorrect S3 permissions
- Incorrect CloudFront origin configuration

##### Solution
Updated S3 bucket policy
Fixed CloudFront origin settings


#### 2. ACM Certificate Pending Validation

##### Cause
- Incorrect DNS validation records
- Duplicate/malformed CNAME records

##### Solution
- Deleted incorrect DNS records
- Recreated proper CNAME validation records in Route 53
- Waited for DNS propagation

##### Result
- Certificate successfully issued
- Verified public access configuration


#### 3. CloudFront Distribution Not Appearing in Route 53

##### Cause
- Alternate domain name not configured
- SSL certificate not attached properly

##### Solution
- Added custom domain in CloudFront
- Attached ACM certificate
- Redeployed CloudFront distribution


#### 4. Website Showing “Not Secure”

##### Cause
- Website accessed over HTTP
- HTTPS redirection not configured

##### Solution
- Enabled HTTPS in CloudFront
- Configured HTTP → HTTPS redirection


### Final Outcome
The project successfully achieved:
- Static website deployment on AWS
- HTTPS secure communication
- Custom domain integration
- Global CDN distribution
- Real-world cloud troubleshooting experience


### Skills Demonstrated
- AWS Cloud Infrastructure
- Static Website Hosting
- CDN Configuration
- DNS Management
- SSL/TLS Certificate Management
- Cloud Troubleshooting
- DevOps Fundamentals


### Real-World Use Cases
This architecture is commonly used for:
- Portfolio websites
- SaaS landing pages
- Corporate websites
- Documentation websites
- High-performance static applications


### Project Status

The live deployment has been stopped due to AWS usage costs incurred during the learning and testing phase.

However, this project remains a complete hands-on implementation of a production-style AWS deployment architecture.

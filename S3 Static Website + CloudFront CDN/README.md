## S3 Static Website + CloudFront CDN Project

This project demonstrates the deployment of a globally distributed static website using Amazon CloudFront as a CDN and Amazon S3. The goal was to build a secure, scalable, and high-performance content delivery setup using AWS.

# Project Overview

in this project, i deployed a static website using:
- Amazon S3 for static file hostin
- CloudFront asa global CDN
- HTTPS delivery via CloudFront
- caching and performance optimisation through edge locations

The architecture ensures fast and secure delivery of website content.


**Architectural Diagram**
<img width="704" height="384" alt="IMG_7951" src="https://github.com/user-attachments/assets/81d4eb8a-1b91-487e-878d-66f3988400f4" />


# S3 Static Website Hosting

I created an S3 bucket to host the static website 

The bucket included:
- index.html as the main landing page
- error.html for error handling
- static website hosting enabled

The website files were configured for public access to allow CloudFront to retrieve content from the origin

**S3 Bucket / index.html error.html**
<img width="1256" height="549" alt="s3 bucket overview" src="https://github.com/user-attachments/assets/5db89b73-8c37-4489-a817-c72d378d9172" />

**Error Path configurations**
<img width="986" height="547" alt="error path" src="https://github.com/user-attachments/assets/cb470cb0-40be-444e-a1f9-9968ffa65c7a" />



# CloudFront Distribution

I created a CloudFront distribution with the S3 bucket as the origin.

The configuration included:
- S3 bucket as the origin
- HTTPS enabled by default
- Default root set to index.html
- Cache behaviour configured for GET and HEAD requests
- Optimised caching policy for performance

CloudFront acts as a CDN, caching content at edge locations for faster delivery.

**CloudFront Origin Overview**
<img width="984" height="487" alt="s3 bucket overview2" src="https://github.com/user-attachments/assets/cc27d1fa-384e-4db0-857d-20391f34b7e5" />


# Testing & Validation

The setup was tested by accessing the CloudFront distribution URL in a web browser.

The website loaded successfully, confirming:
- S3 bucket was correctly configured
- CloudFront was properly connected as a CDN origin
- Content was being delivered through edge locations

**Website Testing**
<img width="953" height="558" alt="s3 websute proof" src="https://github.com/user-attachments/assets/896b05c9-088b-4743-afea-425ca87bac6b" />

























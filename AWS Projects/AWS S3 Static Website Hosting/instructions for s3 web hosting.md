
# AHKU Cafe – Amazon S3 Static Website Hosting Guide

---

## Project Overview

This document describes the steps followed to host the AHKU Cafe static website using Amazon S3 Static Website Hosting as part of the AWS re/Start Portfolio Project.
Amazon S3 was selected as the hosting solution because it is cost-effective, highly available, scalable, and does not require server management—making it ideal for a small café business.

 ---
 
### Prerequisites

Before starting, ensure you have:
•	An active AWS Account
•	A completed static website (HTML/CSS files)
•	The main website file named index.html

 ----
 
### Step 1: Log in to the AWS Management Console

1.	Open a browser and go to https://aws.amazon.com
2.	Click Sign in to the Console
3.	Log in using your AWS account credentials
   <img width="1904" height="791" alt="0" src="https://github.com/user-attachments/assets/94d4094a-fcb0-41d6-bdfd-3e8286d6666c" />

 ---
 
### Step 2: Access Amazon S3

1.	In the AWS Console search bar, type S3
2.	Select Amazon S3
3.	You will be redirected to the S3 dashboard
   <img width="1319" height="842" alt="1" src="https://github.com/user-attachments/assets/42da5eb7-d2e9-49dd-991d-61d421e937d1" />

 ---
 
### Step 3: Create an S3 Bucket

1.	Click Create a bucket
   <img width="438" height="276" alt="2" src="https://github.com/user-attachments/assets/aab6d139-f4f4-4cd9-8641-848289cb8945" />

2.	Enter a globally unique bucket name (bucket name: Ahku-cafe-website)
3.	Select a Region ( Africa (Cape Town)
4.	Leave Object Ownership as default (ACLs disabled) 
   <img width="1612" height="852" alt="3" src="https://github.com/user-attachments/assets/d7bd7b4f-540e-430d-9f01-b89b752c03e6" />

 ---
 
### Step 4: Configure Public Access Settings

1.	Under Block Public Access settings, uncheck:
    o	✅ Block all public access
2.	Acknowledge the warning by ticking the confirmation checkbox
3.	Leave Bucket Versioning disabled
4.	Leave Default Encryption enabled(SSE-S3 enabled)
   <img width="1839" height="623" alt="4" src="https://github.com/user-attachments/assets/39a96884-4a01-4324-9db9-7e824dd5727d" />


5.	Click Create bucket
   <img width="1867" height="314" alt="5" src="https://github.com/user-attachments/assets/22e85568-28c9-4566-825b-30c9f2234184" />

 ---
 
### Step 5: Upload Website Files

1.	Open the newly created bucket
   <img width="1267" height="572" alt="6" src="https://github.com/user-attachments/assets/1ab928e3-7ff5-457c-b978-4fb6f42700ed" />

3.	Click Upload
   <img width="1862" height="361" alt="7" src="https://github.com/user-attachments/assets/09b80d29-0359-4838-b82d-e3e5e3922f76" />

5.	Select Add files
6.	Upload index.html (and any additional files such as images, CSS, or JavaScript)
   <img width="1834" height="571" alt="8" src="https://github.com/user-attachments/assets/0f23c66b-ed8e-4e3d-a0e3-5b649e6e7273" />

8.	Click Upload
   <img width="1860" height="667" alt="10" src="https://github.com/user-attachments/assets/a6d9d191-77b5-4329-a395-b0fa6e57858e" />

---

### Step 6: Enable Static Website Hosting

1.	Go to the Properties tab of the bucket
   <img width="1051" height="82" alt="11" src="https://github.com/user-attachments/assets/764468ff-a3b5-4c4f-a7aa-9ee35c69ab26" />

2.	Scroll to Static website hosting
3.	Click Edit
4.	Select Enable
5.	Choose Host a static website
6.	Enter:
7.	Index document: index.html
   <img width="1834" height="735" alt="12" src="https://github.com/user-attachments/assets/eeb45963-e34d-4eac-b83a-1588b79ef168" />

8.	Click Save changes
   <img width="1851" height="66" alt="13" src="https://github.com/user-attachments/assets/6d86157a-9339-4d11-81e3-3a31fe1c1c06" />

 ---
 
### Step 7: Configure Bucket Policy for Public Access

1.	Go to the Permissions tab
2.	Scroll to Bucket policy
3.	Click Edit
4.	Paste the following policy (replace the bucket name if necessary):
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::ahku-cafe-website/*"
    }
  ]
}

   <img width="1423" height="724" alt="14" src="https://github.com/user-attachments/assets/0d16fc80-a8fd-4dd1-a2eb-98735b0d242e" />

5.	Click Save changes
   <img width="1863" height="535" alt="15" src="https://github.com/user-attachments/assets/3e047a4b-596c-4d64-a6ae-496a7bb32c41" />

 ---

### Step 8: Access the Live Website

1.	Navigate back to the Properties tab
   <img width="1051" height="82" alt="11" src="https://github.com/user-attachments/assets/6b231a4e-2f72-496d-865d-9d10195b0100" />

3.	Scroll to Static website hosting
4.	Copy the Bucket website endpoint
   <img width="1838" height="352" alt="16" src="https://github.com/user-attachments/assets/ee3a4fb7-a307-466a-92b1-d7ea79a4708b" />

6.	Paste the URL into a web browser to view the live AHKU Cafe website
   <img width="1893" height="967" alt="17" src="https://github.com/user-attachments/assets/8c49de9a-3a08-4312-a11d-8e4da3d418f6" />

---
 
## Benefits of Hosting AHKU Cafe on Amazon S3

•	Low Cost: Pay only for storage and usage
•	High Availability: 99.99% availability
•	Scalability: Automatically handles traffic growth
•	No Server Management: AWS fully manages the infrastructure
•	Security: Supports encryption and IAM integration

 ---
# Conclusion
By hosting the AHKU Cafe website on Amazon S3, the business gains a reliable, scalable, and affordable online presence. This solution removes the need for on-premises servers while improving accessibility and customer engagement.
 
---

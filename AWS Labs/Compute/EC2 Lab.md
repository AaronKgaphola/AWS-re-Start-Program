# EC2 Hands-On LAB


## Introduction to Amazon EC2

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.

Amazon EC2's simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon's proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

<img width="479" height="389" alt="image" src="https://github.com/user-attachments/assets/c431240a-86df-4f46-ac4d-523406343e05" />

In this I lab provide you with a basic overview of launching, resizing, managing, and monitoring an Amazon EC2 instance.

---
In the lab I will demonstrate:
-	Launching a web server with termination protection enabled
- Monitoring the EC2 instance
-	Modify the security group that the web server is using to allow HTTP access
-	Resize the Amazon EC2 instance to scale
- Test termination protection
-	Terminate the EC2 instance
  
### This lab has 5 tasks

----

#### TASK 1: Launching your EC2 instance

* Go to the console dashboard either search for EC2 or it will be there on your dashboard to launch it


<img width="1022" height="688" alt="Screenshot 2026-01-29 100352" src="https://github.com/user-attachments/assets/9018f179-7be0-457e-ae2f-17aa6abadb17" />


----
#### STEP 1: Naming your EC2 instance
* Change the instance name to Web Server
  
<img width="1022" height="688" alt="Screenshot 2026-01-29 100352" src="https://github.com/user-attachments/assets/098b03f6-7386-4692-9de7-919a05e18b60" />

### STEP 2: Choosing an Amazon Machine Image (AMI)
* Locate and choose the operating system of AMAZON LINUX 2023
* Keep it as it is, at default

<img width="1231" height="558" alt="Screenshot 2026-01-29 100725" src="https://github.com/user-attachments/assets/9459db72-d4a5-44a3-a1b3-8b10fab1dfe9" />

### STEP 3: Choosing an instance type
* Select a t3.micro instance

<img width="1232" height="303" alt="Screenshot 2026-01-29 100918" src="https://github.com/user-attachments/assets/c729df69-3134-495e-b9ac-98d9d11d10c4" />

### STEP 4: Configuring a key pair
* In the Key pair (login) pane, select Proceed without a key pair (Not recommended)

<img width="1245" height="251" alt="Screenshot 2026-01-29 100952" src="https://github.com/user-attachments/assets/08ee3147-7104-4771-a0e9-3ae3c629d0eb" />

### STEP 5: Configuring the network settings
* For VPC - required, select Lab VPC.
* Security group name - required: Web Server security group
* Description: Security group for my web server
* Under Inbound security groups rules select the Remove

<img width="745" height="231" alt="image" src="https://github.com/user-attachments/assets/3bc1c911-a667-4378-ae8d-b43d7f58723f" />

### STEP 6: Configuring advanced details
* Enable Termination Protection
  
  <img width="994" height="246" alt="image" src="https://github.com/user-attachments/assets/81910f38-1d47-4aa6-ae9f-b075c275ae68" />

* Copy the commands and paste them in the user data box
  
  <img width="749" height="268" alt="image" src="https://github.com/user-attachments/assets/ecb871d6-ae59-46a6-befa-b4dd0571ab03" />

### Step 7: Launching an EC2 instance
* Launch the instance
* Select the  box next to your Web Server
* Review if the instance is running
* Review the if all instace checks are completed
  <img width="1445" height="75" alt="Screenshot 2026-01-29 102326" src="https://github.com/user-attachments/assets/40e364f7-2075-4901-9a90-7f4c734d8aea" />

---
### Task 2: Monitor Your Instance
* Review if the systems reacability is passed
* Review if the instance reachability is passed

<img width="1566" height="327" alt="Screenshot 2026-01-29 102650" src="https://github.com/user-attachments/assets/3d4f8895-f317-4a51-9694-5a1f7d3812fe" />
* Get the isnstance screeenshot
  <img width="633" height="687" alt="Screenshot 2026-01-29 102842" src="https://github.com/user-attachments/assets/42c59775-4ad2-42f8-be74-d1dafe3761a1" />

---
### Task 3: Update Your Security Group and Access the Web Server
* Copy the Public IPv4 address of your instance to your clipboard.
* N.B it will not open, to fix this I changed the indbound rules
* Add a rule with type : HTTP and source: Anywhare-IPv4

<img width="1901" height="372" alt="Screenshot 2026-01-29 103717" src="https://github.com/user-attachments/assets/d341869e-9d82-4519-8c3a-c306d92c9ac5" />

---
### Task 4: Resize Your Instance: Instance Type and EBS Volume
* Stop your instance
  <img width="992" height="593" alt="Screenshot 2026-01-29 104006" src="https://github.com/user-attachments/assets/c996786f-c1ed-4f3b-9115-f982af01dbc5" />

* Change The Instance Type to t3.small
  <img width="1020" height="445" alt="Screenshot 2026-01-29 104309" src="https://github.com/user-attachments/assets/5a3bdbf4-af08-40fa-813f-ad20ff8b2832" />
  
* Resize the EBS Volume from 8 Gb to 10 Gb
  <img width="968" height="699" alt="Screenshot 2026-01-29 104545" src="https://github.com/user-attachments/assets/f57e8006-2267-45d4-901e-7bcaca0f2105" />
  
* Start the Resized Instance
  <img width="1544" height="306" alt="Screenshot 2026-01-29 104844" src="https://github.com/user-attachments/assets/c5390e82-073f-4bae-b22f-73f4760ef6de" />

### Task 5: Test Termination Protection
* Termonating the instance wiht protection will not be proccessed, to change this I changed the Termination Protection settings of the intance
  <img width="1562" height="351" alt="Screenshot 2026-01-29 105135" src="https://github.com/user-attachments/assets/5e61ca9a-e673-46dd-ba74-c03890246064" />
* Disable the termination protection of the instance
  <img width="732" height="464" alt="Screenshot 2026-01-29 105213" src="https://github.com/user-attachments/assets/646e6ad3-2fc1-40de-a3af-afa6a8b46087" />
* After this proccess instance will be termonated
  <img width="1567" height="286" alt="Screenshot 2026-01-29 105429" src="https://github.com/user-attachments/assets/8d3d839f-4caa-4f58-a7e6-831d7d3d4a15" />

## What I Learned
Through this lab, I gained **hands-on experience with EC2 from start to finish**. I learned how to:

- Deploy and secure a web server using automation  
- Use security groups to control network traffic effectively  
- Monitor instance health and performance using CloudWatch  
- Scale compute and storage resources dynamically  
- Implement safeguards like termination protection to prevent accidental loss  

Overall, this experience deepened my understanding of **cloud infrastructure management** and gave me practical insight into building **resilient and scalable applications on AWS**.

--- 

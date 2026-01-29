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
###### STEP 1: Naming your EC2 instance
* Change the instance name to Web Server
  
<img width="1022" height="688" alt="Screenshot 2026-01-29 100352" src="https://github.com/user-attachments/assets/098b03f6-7386-4692-9de7-919a05e18b60" />



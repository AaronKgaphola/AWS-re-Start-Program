# Build a VPC and Launch a Web Server
----

## Overview
-	Create a virtual private cloud (VPC)
-	Create subnets
-	Configure a security group
-	Launch an Amazon Elastic Compute Cloud (Amazon EC2) instance into a VPC
------
##### Task 1: Create the VPC

In this task, I use the VPC Wizard to create a VPC, an internet gateway, and two subnets in a single Availability Zone. An internet gateway is a VPC component that allows communication between instances in my VPC and the internet.

VPC settings:

   <img width="604" height="666" alt="Screenshot 2026-03-08 164156" src="https://github.com/user-attachments/assets/8935581d-8087-4cd2-8213-9d480b869276" />


&nbsp;

Here I set the correct number of AZ's needed, added 1 public subnet and 1 private subnet, customized the CIDR blocks for both subnets.

   <img width="604" height="748" alt="Screenshot 2026-03-08 164400" src="https://github.com/user-attachments/assets/15add05a-d34d-4177-b5ba-d17ae675930a" />


&nbsp;

Here I created a NET Gateway in one AZ, then set the it with no VPC endpoints.

   <img width="603" height="748" alt="Screenshot 2026-03-08 164505" src="https://github.com/user-attachments/assets/9b59a9d5-70e2-4a2d-83e2-b9f766569c67" />


&nbsp;

I’ve configured the preferred settings, named my VPC ,route tables, and subnets accordingly below.

   <img width="700" height="370" alt="image" src="https://github.com/user-attachments/assets/a5b3a2d6-46b3-4198-86b1-8b8be792dbf4" />


&nbsp;

Click create VPC and wait for the following the all be checked.

   <img width="1879" height="724" alt="Screenshot 2026-03-08 164710" src="https://github.com/user-attachments/assets/1bc66b05-3d79-4abf-9d72-95325ecbebf9" />


&nbsp;

My VPC is now available for use:

   <img width="900" height="190" alt="image" src="https://github.com/user-attachments/assets/56f1fa91-1777-4b32-bd81-2270203f56f7" />


-----
#### Task 2: Create additional subnets

In this task, I create two additional subnets in a second Availability Zone. This option is useful for creating resources in multiple Availability Zones to provide high availability.

   <img width="1600" height="158" alt="Screenshot 2026-03-08 170331" src="https://github.com/user-attachments/assets/7d42dada-7e19-4a8e-a75d-4722fecd0b5c" />


&nbsp;

I've associated the new public subnet with Public route.

   <img width="1590" height="664" alt="Screenshot 2026-03-08 171102" src="https://github.com/user-attachments/assets/dc919afb-cdcc-488c-8978-3be311f8fa6f" />


&nbsp;

I've associated the new private subnet with Private route.

   <img width="1578" height="674" alt="Screenshot 2026-03-08 171144" src="https://github.com/user-attachments/assets/819f8c7d-10cb-44be-a14a-85ab10fb0735" />


&nbsp;

My VPC now has public and private subnets configured in two Availability Zones:

   <img width="860" height="400" alt="image" src="https://github.com/user-attachments/assets/ca8d608c-3842-4e4a-b93d-856854dc730d" />

-----
#### Task 3: Create a VPC Security Group

In this task, I have created a VPC security group, which acts as a virtual firewall for my instance. When you launch the instance, you associate one or more security groups with the instance. You can add rules to each security group that allow traffic to or from its associated instances.

   <img width="1880" height="697" alt="Screenshot 2026-03-08 171511" src="https://github.com/user-attachments/assets/c368bcb8-737b-4d8b-9e62-036394cfa6d5" />


------
#### Task 4: Launch a Web Server Instance

In this task, I launch an EC2 instance into the new VPC. I configure the instance to act as a web server.

   <img width="1249" height="288" alt="Screenshot 2026-03-08 171808" src="https://github.com/user-attachments/assets/3bb10bee-7646-4a73-9a26-68a274d90231" />


&nbsp;
Select the correct OS and AMI

   <img width="1218" height="701" alt="Screenshot 2026-03-08 171916" src="https://github.com/user-attachments/assets/71654937-8867-4bb0-b96e-748383b2b3c6" />


 &nbsp;

Select the instance type: t3.micro and the key pair:

   <img width="1219" height="546" alt="Screenshot 2026-03-08 171956" src="https://github.com/user-attachments/assets/f0089d20-77ee-42a9-82f5-63d6ed22ea6e" />


 &nbsp;

Selected the correct VPC, subnet, enable the auto assign IP and security group.
 
   <img width="1207" height="676" alt="Screenshot 2026-03-08 172106" src="https://github.com/user-attachments/assets/ee55b243-34db-4d4d-9c57-3869bf19168b" />

Add the correct user data.

   <img width="772" height="527" alt="Screenshot 2026-03-08 172243" src="https://github.com/user-attachments/assets/63cf2178-cf98-431b-8f13-b0d475dfcc4b" />


  &nbsp;

Launch the Instance.

   <img width="582" height="629" alt="Screenshot 2026-03-08 172307" src="https://github.com/user-attachments/assets/fbd5242b-9ef1-4a75-9498-c16759821a22" />


------
#### Task 5: Connect to the web server running on the EC2 instance

-	Select the check box for the instance and choose the **Details tab.**
-	copy the **Public IPv4 DNS value.**
-	open a new web browser tab, paste the Public IPv4 DNS value, 

The web server application loaded successfully, confirming the instance and VPC configuration were working correctly.

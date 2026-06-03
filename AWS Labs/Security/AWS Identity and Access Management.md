# AWS Identify and Access Management
------
### Objectives
-	Create and apply an IAM password policy
-	Explore pre-created IAM users and user groups
-	Inspect IAM policies as applied to the pre-created user groups
-	Add users to user groups with specific capabilities active
-	Locate and use the IAM sign-in URL
-	Experiment with the effects of policies on service access

-----
### IAM can be used for the following:
-	_Manage IAM users and their access:_ You can create users and assign them individual security credentials (access keys, passwords, and multi-factor authentication devices). You can manage permissions to control which operations a user can perform.
-	_Manage IAM roles and their permissions:_ An IAM role is similar to a user in that a role is an AWS identity with permission policies that determine what the identity can and cannot do in Amazon Web Services (AWS). However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it.
-	_Manage federated users and their permissions:_ You can activate identity federation to allow existing users in your enterprise to access the AWS Management Console, to call AWS application programming interfaces (APIs), and to access resources without the need to create an IAM user for each identity.
----- 
#### Task 1: Creating an account password policy

<img width="1381" height="841" alt="iam1" src="https://github.com/user-attachments/assets/3cbd06dd-2748-4b5e-83ec-2e64fcaa09d4" />

&nbsp;

 On the dashboard under _account settings_, I clicked “edit”
 
<img width="1904" height="579" alt="iam2" src="https://github.com/user-attachments/assets/28150ae0-5393-4fe0-9f97-121d74f0a35f" />

&nbsp;

My new password policies:

<img width="1845" height="752" alt="iam3" src="https://github.com/user-attachments/assets/342b92f3-d05e-4acd-8cf7-2ba05dfba2e9" />

&nbsp;

<img width="940" height="330" alt="image" src="https://github.com/user-attachments/assets/2dba5bea-2514-47bb-bf23-e464594b1f87" />

-----
#### Task 2: Explore users and user groups

Available users:

<img width="1917" height="445" alt="iam4" src="https://github.com/user-attachments/assets/1ef88e59-8ae3-4dec-bc94-55d71dbdfe7e" />

&nbsp;

Available user groups:
<img width="900" height="200" alt="image" src="https://github.com/user-attachments/assets/a9425f6f-1767-46b1-8628-82e5233a027d" />


------
A **policy** defines what actions are allowed or denied for specific AWS resources. This policy grants permission to list and describe information about Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudWatch, and Amazon EC2 Auto Scaling. This ability to view resources but not modify them is ideal for assigning to a support role.
The following is the basic structure of the statements in an IAM policy:
- **Effect** indicates whether to **Allow** or **Deny** the permissions.
- **Action**specifies the API calls that can be made against an AWS service (for example, cloudwatch:ListMetrics).
- **Resource** defines the scope of entities covered by the policy rule (for example, a specific Amazon Simple Storage Service [Amazon S3] bucket, EC2 instance, or  which means any resource).
- 


-----
#### Task 3: Add users to user groups

_Add user-1 to the S3 support_
<img width="1556" height="708" alt="iam5" src="https://github.com/user-attachments/assets/50a820c4-21a6-4785-badd-1af744a049c5" />

_User 2 added to  EC2 support_
<img width="1541" height="705" alt="iam6" src="https://github.com/user-attachments/assets/4ee601ff-cb59-4c9e-a368-370a2716f786" />

_User 3 added to EC2 Admin_
<img width="940" height="300" alt="image" src="https://github.com/user-attachments/assets/7ac139ab-079e-499f-941a-d9094d609b1c" />

------
#### Task 4: Sign in and test user permissions

On the dashboard a link is provided. I copied the link and opened a new incognito tab to test the user permissions
<img width="1565" height="669" alt="iam8" src="https://github.com/user-attachments/assets/dc29f9ab-1ca2-4c25-a8de-9a12bdaa0b40" />


------
#### User 1
<img width="1558" height="885" alt="iam9" src="https://github.com/user-attachments/assets/44fb524c-75a2-4559-b81a-b24ab8fbea07" />


User 1 is able to see S3 buckets as they have been added to the group.
<img width="1919" height="804" alt="iam10" src="https://github.com/user-attachments/assets/628c2d56-5b89-4871-be70-0e1ac79e09aa" />

User 1 does not have access to the EC2 uspport or admin groups to view instances.
<img width="1897" height="803" alt="iam11" src="https://github.com/user-attachments/assets/187abc16-92f7-461e-852a-94a9fb06d022" />


&nbsp;

----
#### User 2
<img width="1545" height="891" alt="iam12" src="https://github.com/user-attachments/assets/324d4195-781c-4ef4-9a61-4b6f9789fbf2" />

User 2 is able to see an EC2 instance because they have read-only permissions. However, aren’t able to make any changes to Amazon EC2 resources.
<img width="1898" height="859" alt="iam14" src="https://github.com/user-attachments/assets/4419f709-cf7e-474c-8fc6-ecb684719e2f" />

User 2 is not able to stop the instance as the only have read permissions.
<img width="1605" height="372" alt="iam15" src="https://github.com/user-attachments/assets/c26d5709-7a44-4de3-93b1-6c7cf679e571" />

User 2 doesn’t have access to list and view s3 buckets
<img width="1918" height="622" alt="iam16" src="https://github.com/user-attachments/assets/74b28afc-8c11-4778-9ac6-d1c5fd5804df" />

---
#### User 3
<img width="1544" height="889" alt="iam17" src="https://github.com/user-attachments/assets/80fc84ef-cb27-42cd-833a-bdad53a85f3c" />

User 3 was able to stop the EC2 instance as they have the permission to do so
<img width="1600" height="375" alt="iam19" src="https://github.com/user-attachments/assets/10097bce-6132-4214-842e-13bd268dfce0" />


-------
I successfully:
-	Created and applied an IAM password policy
-	Explored pre-created IAM users and user groups
-	Inspected IAM policies as applied to the pre-created user groups
-	Added users to user groups with specific capabilities active-
-	Located and used the IAM sign-in URL
-	Experimented with the effects of policies on service access
 

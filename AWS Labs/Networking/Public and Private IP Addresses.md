
Public and private IP addresses
-----

**Objectives:**

In this lab, i will:
- Summarize and investigate the customer scenario
- Analyze the difference between a private and public IP address
- Develop a solution to the customer's issue in this lab
- Summarize and describe my findings

-------
1. I navigated to the Amazon EC2 dashboard. On the left pane, I choose Instances. This option took me to my current EC2 instances.
   <img width="1567" height="372" alt="Screenshot 2026-03-04 112815" src="https://github.com/user-attachments/assets/e90a26a3-b942-45db-81e4-a8d7b40396eb" />


2.  Select the check box next to instance A. At the bottom of the page, choose the _Networking tab_, and note the Public and Private IPv4 addresses:
   
   - Instance A has only the private IP address
     <img width="1603" height="436" alt="Screenshot 2026-03-04 112919" src="https://github.com/user-attachments/assets/fdfd79c4-2cf3-4465-bdfe-2185ef7e4ec2" />



   - Instance B has both the private and public IPv4 address
     <img width="1581" height="438" alt="Screenshot 2026-03-04 112956" src="https://github.com/user-attachments/assets/aedf0b78-22b1-416b-962a-845191167a98" />


----
**Using SSH to connect to an Amazon Linux EC2 instance**

1. I connected to a Amazon Linux EC2 instance using an SSH utility to perform all of these operations.
   -For Instance B it connected since it has a public IP address.
   
      <img width="818" height="512" alt="Screenshot 2026-03-04 113503" src="https://github.com/user-attachments/assets/38a851fa-6ed3-4ca2-bf77-9462aeee5fd5" />

   -For Instance A it did not connect because it has a private IP address.
      <img width="977" height="519" alt="Screenshot 2026-03-04 113805" src="https://github.com/user-attachments/assets/81149384-7898-4e2f-a734-16c8d404e2dd" />

&nbsp;

After connecting to the Amazon Linux EC2 instance, I noticed that I was not able to connect to Instance A because it was assigned only a private IP address. Private IP addresses cannot be accessed from outside the VPC. Since I was attempting to connect from outside the VPC, the connection was not possible.
However, I was able to connect to Instance B because it had a public IP address assigned to it. The public IP allowed access from outside the VPC, which enabled me to successfully use the SSH utility to connect to the instance.

**Conclusion:**

In this lab, I investigated the customer’s environment and applied troubleshooting techniques that allowed me to resolve the customer’s issue. During the scenario, I discovered that the customer’s EC2 instance (Instance A) needed a public IP address in order to connect to the internet. I tested this by attempting to use an SSH utility to connect to the instance.
I found that private IP addresses are used only within the VPC and cannot establish a connection to the internet. Because Instance A only had a private IP address, it was not accessible externally. I also learned that using a public range of IP addresses for a VPC can cause complications, such as receiving replies from unrelated external resources, which can lead to networking conflicts and unexpected behaviour.


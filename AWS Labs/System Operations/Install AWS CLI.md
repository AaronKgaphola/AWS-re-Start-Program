Install and Configure the AWS CLI
-----

**Lab overview**

The AWS Command Line Interface (AWS CLI) is a command line tool that provides an interface for interacting with products and services from Amazon Web Services (AWS).

-------
**Objectives**
-	Install and configure the AWS CLI.
-	Connect the AWS CLI to an AWS account.
-	Access IAM by using the AWS CLI.

------
_**Task 1: Connect to the Red Hat EC2 instance by using SSH**_

1. In this task, I need to log into an existing EC2 instance.
<img width="596" height="537" alt="Screenshot 2026-04-02 132302" src="https://github.com/user-attachments/assets/09d2b51a-db37-487c-9df9-8947e57fe852" />

2. After inserting the needed information for the connection, I clicked open and entered my username.
<img width="822" height="518" alt="Screenshot 2026-04-02 132457" src="https://github.com/user-attachments/assets/15aa50c9-d133-4941-aab5-f472bc898f0c" />

-------
_**Task 2: Install the AWS CLI on a Red Hat Linux instance**_

1. To write the downloaded file to the current directory, I ran the following curl command with the -o option:

**Curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"**

<img width="600" height="500" alt="Image" src="https://github.com/user-attachments/assets/d2c957d5-a9b5-4eb4-9836-0acabd71072a" />

&nbsp;

2. To unzip the installer, I ran the unzip command with the **-u option**. In this command, the unzip command prompts you to overwrite any existing files. To skip these prompts, the command includes the -u option.

**unzip -u awscliv2.zip**

The result:

<img width="600" height="556" alt="Image" src="https://github.com/user-attachments/assets/36803d79-5e4a-4e58-a113-0192a92e66b8" />

&nbsp;

3. I ran the below command to install the program. This sudo command grants write permissions to the directory. The installation command in the code snippet uses a file named install in the unzipped aws directory to install the AWS CLI. 

**sudo ./aws/install.**

<img width="500" height="165" alt="Image" src="https://github.com/user-attachments/assets/1d003122-91a2-4f2a-811b-972b98a5bf0f" />

&nbsp;

4. My CLI is now working

<img width="500" height="539" alt="Image" src="https://github.com/user-attachments/assets/63655975-0360-49b5-9d6a-9255b990a04f" />

-----
_**Task 3: Observe IAM configuration details in the AWS Management Console**_

In this section, I observe the IAM configuration details for the EC2 instance in the AWS Management Console. 

1. In the AWS Management Console, I navigated to the IAM service.

<img width="500" height="353" alt="Image" src="https://github.com/user-attachments/assets/5bc02c0c-8efa-46b0-8e50-571fd0e520f9" />

&nbsp;

2. In the navigation pane, under **Users**, I chose **awsstudent**.
 
3. this lead me to the **Permissions** tab. 
<img width="1521" height="752" alt="Screenshot 2026-04-02 132906" src="https://github.com/user-attachments/assets/7d21125d-272b-4200-ac8f-18201762a0ca" />

&nbsp;

4. This **lab_policy** document is formatted in JSON. The IAM policy grants the awsstudent user access to specific AWS services in this account.

<img width="500" height="370" alt="Image" src="https://github.com/user-attachments/assets/8ddc6a8a-dc4c-4c83-a8de-7ddc650f85e1" />

&nbsp;

5. In the **Security credentials** tab, I navigated to the **Access keys** section to  locate the awsstudent user's access key ID
<img width="1489" height="735" alt="Screenshot 2026-04-02 133236" src="https://github.com/user-attachments/assets/80c85821-42e2-48ef-b892-53ba626128e6" />

------
_**Task 4: Configure the AWS CLI to connect to your AWS Account**_

1. In the SSH session terminal window, I ran the configure command for the AWS CLI:
**aws configure**

2. At the prompt, I configured the following:
- AWS Access Key ID: 
- AWS Secret Access Key:
- Default region name:  
- Default output format: 

(NOT SHOWN)

----
_**Task 5: Observe IAM configuration details by using the AWS CLI**_

In this section, I observe the IAM configuration details for the EC2 instance using the AWS CLI.
1. In the terminal window, test the IAM configuration by running the following command:
**aws iam list-users**
A successful test shows a JSON response that includes a list of IAM users in the account.
<img width="1307" height="351" alt="Screenshot 2026-04-02 134105" src="https://github.com/user-attachments/assets/c2a875da-b0bc-4585-978e-a662128f831a" />

&nbsp;

The following command lists IAM policies and filters customer managed policies:
<img width="1323" height="518" alt="Screenshot 2026-04-02 134139" src="https://github.com/user-attachments/assets/98b10679-65f8-456a-9de3-347c28cdb9e0" />

------
_**Conclusion**_

The following has been completed:
-	Installed and configured the AWS CLI
-	Connected the AWS CLI to an AWS account
-	Accessed IAM by using the AWS CLI

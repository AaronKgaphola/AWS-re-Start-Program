**Monitor an EC2 Instance**
----
**Lab overview**

Logging and monitoring are techniques implemented to achieve a common goal. They work together to help ensure that a system's performance baselines and security guidelines are always met. 

**Logging** refers to recording and storing data events as log files. Logs contain low-level details that can give you visibility into how your application or system performs under certain circumstances. From a security standpoint, logging helps security administrators identify red flags that are easily overlooked in their system.

**Monitoring** is the process of analyzing and collecting data to help ensure optimal performance. Monitoring helps detect unauthorized access and helps align your services' usage with organizational security.

**Objectives**
-	Create an Amazon SNS notification
-	Configure a CloudWatch alarm
-	Stress test an EC2 instance
-	Confirm that an Amazon SNS email was sent
-	Create a CloudWatch dashboard

_The lab environment includes one preconfigured EC2 instance named **Stress Test** with an attached AWS Identity and Access Management (IAM) role that you can use to connect via AWS Systems Manager session manager._

----
_**Task 1: Configure Amazon SNS**_

1. In the AWS management consol, search _SNS_
<img width="1176" height="779" alt="Screenshot 2026-03-14 231809" src="https://github.com/user-attachments/assets/e3b0bfc5-631e-42f7-b7e4-aed3bfb0e3bc" />


&nbsp;

2. Choose _create topic_
<img width="1919" height="458" alt="Screenshot 2026-03-14 231903" src="https://github.com/user-attachments/assets/88518aef-d6b4-4db3-91f3-173974fa9718" />

On the Create topic page in the **Details** section, configure the following options:
-	Type: Choose Standard.
-	Name: MyCwAlarm
<img width="1902" height="808" alt="Screenshot 2026-03-14 232009" src="https://github.com/user-attachments/assets/2d182b0a-ce2e-4c93-81f7-f23631976f79" />

&nbsp;

3. On the **MyCwAlarm** details page, choose the **Subscriptions** tab, and then choose **Create subscription**.
4. On the Create subscription page in the Details section, configure the following options:
-  _topic ARN:_ default option.
- _Protocol:_ From the dropdown list, choose **Email.**
- _Endpoint:_ Enter a valid email address that you can access.
<img width="1897" height="799" alt="Screenshot 2026-03-14 232207" src="https://github.com/user-attachments/assets/8fce2b27-76a2-4e35-b2fd-ef7af0d597c7" />

&nbsp;

<img width="1567" height="225" alt="Screenshot 2026-03-14 232257" src="https://github.com/user-attachments/assets/22df09d7-3058-4ebf-8a8b-8c6df2cd2340" />

&nbsp;

5. Open the email received with the Amazon SNS subscription notification and Confirm subscription.
<img width="692" height="340" alt="Screenshot 2026-03-14 232333" src="https://github.com/user-attachments/assets/4a2b1c62-4507-46f8-822a-89294f680986" />

6.	Go back to the AWS Management Console. In the left navigation pane, choose Subscriptions.
The **Status** should now be **Confirmed.**
<img width="1565" height="262" alt="Screenshot 2026-03-14 232353" src="https://github.com/user-attachments/assets/161ee02e-0035-4a83-a45f-2c2b1ecf60b8" />

-----
_**Task 2: Create a CloudWatch alarm**_

**CloudWatch** is a monitoring and observability service built for DevOps engineers, developers, site reliability engineers (SREs), IT managers, and product owners. CloudWatch provides you with data and actionable insights to monitor your applications, respond to system-wide performance changes, and optimize resource utilization. CloudWatch collects monitoring and operational data in the form of logs, metrics, and events. You get a unified view of operational health and gain visibility of your AWS resources, applications, and services running on AWS and on premises.

1. In the AWS Management Console, enter **Cloudwatch** in the search bar, and then choose it.
<img width="1182" height="842" alt="Screenshot 2026-03-14 232444" src="https://github.com/user-attachments/assets/d43e810f-b9cd-4400-bfff-f327aa87c539" />

2. In the left navigation pane, choose the **Metrics** dropdown list, and then choose **All metrics.**
3. On the Metrics page, choose **EC2**, and choose **Per-Instance Metrics.**
From this page, you can view all the metrics being logged and the specific EC2 instance for the metrics.
<img width="1598" height="749" alt="Screenshot 2026-03-14 232602" src="https://github.com/user-attachments/assets/480d6a08-9b03-47f6-b839-abc23637a121" />


&nbsp;

5. Select the check box with **CPUUtilization** as the Metric name for the Stress Test EC2 instance.
<img width="1744" height="848" alt="Screenshot 2026-03-14 232857" src="https://github.com/user-attachments/assets/02b09984-8cea-46c1-b348-0343b236eee9" />

&nbsp;

6. In the left navigation pane, choose the **Alarms** dropdown list, and then choose All alarms.
_A metric alarm watches a single CloudWatch metric or the result of a math expression based on CloudWatch metrics. The alarm performs one or more actions based on the value of the metric or expression relative to a threshold over a number of time periods. The action then sends a notification to the SNS topic that you created earlier._
7. Choose **Create alarm**.
8. Choose **Select metric**, choose EC2, and then choose **Per-Instance Metrics**.
<img width="940" height="273" alt="image" src="https://github.com/user-attachments/assets/f19a96d2-e099-4829-84c8-86dd258748af" />

&nbsp;

9. Select the check box with CPUUtilization as the Metric name for the Stress Test instance name.
10. Choose Select metric.
11. On the **Specify metric and conditions** page,I configured the following options:

**Metric**

•	Metric name: CPUUtilization

•	InstanceId: default option selected.

•	Statistic: Enter Average

•	Period: From the dropdown list, chose 1 minute.
<img width="1498" height="741" alt="Screenshot 2026-03-14 233018" src="https://github.com/user-attachments/assets/c6d2ebbb-e26a-4f8e-b906-3220733d21fa" />

&nbsp;

**Conditions**

•	Threshold type: Static.

•	Whenever CPUUtilization is...: Choose Greater > threshold.

•	than... Define the threshold value: 60
<img width="1475" height="536" alt="Screenshot 2026-03-14 233116" src="https://github.com/user-attachments/assets/cda314df-ca02-4f80-91ea-65cb728b7347" />

&nbsp;

**Notification**

•	Alarm state trigger:  In alarm.

•	Select an SNS topic: Select an existing SNS topic.

•	Send a notification to...: Choose the text box and then choose MyCwAlarm.
<img width="1485" height="729" alt="Screenshot 2026-03-14 233225" src="https://github.com/user-attachments/assets/0cf3e4f4-fb8d-41da-bb2a-f27fa4a06a9b" />

&nbsp;

**Name and description**

•	Alarm name: LabCPUUtilizationAlarm

•	Alarm description - optional: CloudWatch alarm for Stress Test EC2 instance CPUUtilization
<img width="1492" height="563" alt="Screenshot 2026-03-14 233322" src="https://github.com/user-attachments/assets/137f65ff-e903-42f4-88fe-59add757949f" />

&nbsp;

12.	Review the Preview and create page, and then choose Create alarm.
<img width="940" height="220" alt="image" src="https://github.com/user-attachments/assets/13cee55a-76a3-4e6d-bb7c-e8979542b2e1" />

-----

_**Task 3: Test the Cloudwatch alarm**_

In this task, I log in to the Stress Test EC2 instance and run a command that stresses the CPU load to 100 percent. This increase in CPU utilization activates the CloudWatch alarm, which causes Amazon SNS to send an email notification to the email address associated with the SNS topic.
1. Navigate to the Vocareum(Lab instructions) console page and select the **AWS Details** button.
2. Next to EC2InstanceURL, there is a link. Copy and paste this link into a new browser tab.
   <img width="399" height="460" alt="image" src="https://github.com/user-attachments/assets/d21ab70c-4f7b-4c0e-9654-b1b3c97ea0eb" />

&nbsp;

This link connects to the **Stress Test** EC2 instance.

3. To manually increase the CPU load of the EC2 instance, I ran the following command:

**sudo stress --cpu 10 -v --timeout 400s**

The output from the command:

<img width="470" height="300" alt="image" src="https://github.com/user-attachments/assets/5a600971-9c47-47d7-8855-68d50ad92287" />

&nbsp;

4. Copy and paste the URL text next to EC2InstanceURL into another new browser tab to open a second terminal for the Stress Test instance.
   <img width="530" height="470" alt="image" src="https://github.com/user-attachments/assets/6923bed3-baa0-4b1c-aa58-8c038f13142d" />

&nbsp;

run the following command:

**top**

_This command shows the live CPU usage_

<img width="578" height="420" alt="image" src="https://github.com/user-attachments/assets/0eef2b3c-58d8-4640-8776-d67982695b60" />

&nbsp;

5. Navigate back to the AWS console CloudWatch Alarms page
6. Choose **LabCPUUtilizationAlarm.**
7. Monitor the graph while selecting the refresh button every minute until the alarm status is **In alarm**.
8. It takes a few minutes for the alarm status to change to **In alarm** and for an email to send.
<img width="940" height="158" alt="image" src="https://github.com/user-attachments/assets/722fd472-8b8b-486b-b53d-05c2d2577de6" />

&nbsp;

On the graph, you can see where **CPUUtilization** has increased above the 60 percent threshold.
<img width="830" height="340" alt="image" src="https://github.com/user-attachments/assets/d28ccf49-1024-4730-bb5e-14741010b9dd" />

&nbsp;

9. Navigate to your email inbox for the email address that you used to configure the Amazon SNS subscription. You should see a new email notification from **AWS Notifications.**
<img width="734" height="450" alt="image" src="https://github.com/user-attachments/assets/dea1e559-4069-4f94-88ac-ec7eb8e34584" />

----
_**Task 4: Create a CloudWatch dashboard**_

In this task, I create a CloudWatch dashboard using the same CPUUtilization metrics that I have used throughout this lab.

_CloudWatch dashboards are customizable home pages in the CloudWatch console that you can use to monitor your resources in a single view. With CloudWatch dashboards, you can even monitor resources that are spread across different Regions. You can use CloudWatch dashboards to create customized views of the metrics and alarms for your AWS resources._

1. I navigated to the CloudWatch section in the AWS console. In the left navigation pane, choose **Dashboards.**
2. I chose **Create dashboard.**
3. For **Dashboard name**:LabEC2Dashboard and then **Create dashboard.**
4. Select **Line**.
5. Click **Metrics.**
6. I clicked **EC2**, and then choose **Per-Instance Metrics.**
7. Select the check box with **Stress Test** for the Instance name and **CPUUtilization** for the Metric name.
8. Choose Create widget.
9.Clicked **Save dashboard.**

Now I have created a quick access shortcut to view the **CPUUtilization** metric for the **Stress Test** instance.
<img width="940" height="440" alt="image" src="https://github.com/user-attachments/assets/4ca8651e-cd1e-4661-8408-f1d8a44bdbad" />

&nbsp;

<img width="525" height="420" alt="image" src="https://github.com/user-attachments/assets/163b2728-e10b-4cf1-b0f4-b7eff68b0977" />

----
_**Lab summary**_

In this lab, I created a CloudWatch alarm that activated when the Stress Test instance exceeded a specific CPU utilization threshold and a subscription using Amazon SNS that sent an email to me if this alarm goes off. I logged in to the EC2 instance and ran a stress test command that spiked the EC2 instance to 100 percent CPU utilization.
This test simulated what could happen if a malicious actor were to gain control of an EC2 instance and spike CPU utilization. CPU spiking has various possible causes, one of which is malware.

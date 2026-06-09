Working with amazon EBS
---

**Objectives**
- Create an EBS volume.
- Attach and mount an EBS volume to an EC2 instance.
- Create a snapshot of an EBS volume.
- Create an EBS volume from a snapshot.
----
_**Task 1: Creating a new EBS volume**_

In this task, I created and attached an EBS volume to a new EC2 instance.
1.	I opened the AWS Management Console and, in the search bar, entered and selected Amazon EC2 to access the EC2 Management Console. 
2.	In the left navigation pane, I selected Instances.
I observed that an EC2 instance named **Lab**  had already been launched for the lab. 
3.	I noted the Availability Zone for the Lab instance, which appeared similar to us-west-2a. 
4.	In the left navigation pane, under Elastic Block Store, I selected Volumes.
I observed an existing (8 GiB) volume that the EC2 instance was already using. 
5.	I selected Create volume and configured the following options:
-	Volume type: I chose **General Purpose SSD (gp2).** 
-	Size (GiB): I entered **1**, noting that there may be restrictions on creating larger volumes. 
-	Availability Zone: I selected the same Availability Zone as my EC2 instance **(us-west-2a)**. 
<img width="1870" height="743" alt="Screenshot 2026-04-05 181925" src="https://github.com/user-attachments/assets/e2b08863-905f-411a-b3bb-0c2f1a620500" />

&nbsp;
6.	In the **Tags -optional** section, I selected **Add tag**, and configured the following options:
-	Key: Enter Name.
-	Value: i entered **My Volume**.
  
<img width="940" height="192" alt="image" src="https://github.com/user-attachments/assets/df093ca2-4016-4de9-bfcd-0198849236bf" />

7.	Choose **Create volume**.   
A new volume appears with the status of _Creating_ in the **Volume state** column. This status soon changed to _Available_
<img width="1602" height="747" alt="Screenshot 2026-04-05 182030" src="https://github.com/user-attachments/assets/331c9a02-acbf-47e9-acd1-322f0a9e13fb" />

-----
_**Task 2: Attaching the volume to an EC2 instance**_

In this task, I attached my new volume to an EC2 instance.
1. I selected **My Volume.** 
2. From the **Actions** menu, I chose **Attach volume.**
<img width="1586" height="528" alt="Screenshot 2026-04-05 182120" src="https://github.com/user-attachments/assets/be2f261c-165a-45b2-a9ed-c9e03baa3409" />

&nbsp;
3. From the Instance dropdown list, I selected the _Lab_ instance. 
- For the Device name field, I selected **/dev/sdb**, as the commands I would run later in the lab use this device identifier. 
<img width="1895" height="754" alt="Screenshot 2026-04-05 182237" src="https://github.com/user-attachments/assets/b7dbbed8-cac7-4a45-9c09-9d734c693920" />

&nbsp;
4.	Chose **Attach volume**.
The Volume state of my new volume is now In-use.
<img width="1602" height="749" alt="Screenshot 2026-04-05 182303" src="https://github.com/user-attachments/assets/a8142d09-3d41-4e22-ba5d-20f45d6d28fa" />

-----
_**Task 3: Connecting to the EC2 instance**_

In this task, I used EC2 Instance Connect to connect to the Lab EC2 instance.

1. I opened the AWS Management Console and, in the search bar, entered and selected Amazon EC2 to access the EC2 Management Console.
2. In the navigation pane, I selected **Instances**.
3. From the list of instances, I selected the **Lab instance**.
4. I chose **Connect**.
5. On the EC2 Instance Connect tab, I selected Connect, which opened a new browser tab with the EC2 Instance Connect terminal window.

-----
_**Task 4: Creating and configuring the file system**_

In this task, I added the new volume to a Linux instance as an ext3 file system under the /mnt/data-store mount point.

1. To view the storage available on my instance, I ran the following command in the EC2 Instance Connect terminal:
   - ```df -```

2. I observed output similar to the following, which showed the original 8 GB disk volume. My new volume was not yet displayed.
I observed output similar to the following:

```
devtmpfs        464M     0  464M   0% /dev
tmpfs           473M     0  473M   0% /dev/shm
tmpfs           473M  464K  472M   1% /run
tmpfs           473M     0  473M   0% /sys/fs/cgroup
/dev/nvme0n1p1  8.0G  1.7G  6.4G  21% /
tmpfs            95M     0   95M   0% /run/user/0
tmpfs            95M     0   95M   0% /run/user/1000
```

3. To create an ext3 file system on the new volume, I ran the following command:
   - ```sudo mkfs -t ext3 /dev/sdb```
  
4. To create a directory to mount the new storage volume, I ran the following command:
   - ```sudo mkdir /mnt/data-store```

5. To mount the new volume, I ran the following commands:
```
   - sudo mount /dev/sdb /mnt/data-store
   - echo "/dev/sdb /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```

_The last command ensures that the volume is automatically mounted even after the instance is restarted._

6. To view the configuration file and confirm the settings on the last line, I ran the following command:
  - ```cat /etc/fstab```

7. To view the available storage again, I ran the following command:
   - ```df -h```

I observed that the output now included an additional line representing the newly mounted volume.
<img width="695" height="199" alt="Screenshot 2026-04-05 182716" src="https://github.com/user-attachments/assets/7e8903f2-6a26-47aa-90bc-3272c83d9a3d" />

8. To create a file and add text to the mounted volume, I ran the following command:
   - ```sudo sh -c "echo some text has been written > /mnt/data-store/file.txt" ```

9. To verify that the text had been written to my volume, I ran the following command:
    - ```cat /mnt/data-store/file.txt```

I observed that the output displayed the text that was written to the file.
<img width="1458" height="559" alt="Screenshot 2026-04-05 182825" src="https://github.com/user-attachments/assets/1a65d6f0-86c0-4796-8f1a-e973a3699e68" />


------
_**Task 5: Creating an Amazon EBS snapshot**_

In this task, I created a snapshot of my EBS volume.

_Amazon EBS snapshots are stored in Amazon S3 for durability. I understand that new EBS volumes can be created from snapshots for cloning or restoring backups, and that snapshots can also be shared across AWS accounts or copied between regions._

1. On the **EC2 Management Console**, I selected **Volumes** and chose **My Volume**.
2. From the Actions menu, I selected **Create snapshot**.
<img width="1577" height="491" alt="Screenshot 2026-04-05 183104" src="https://github.com/user-attachments/assets/571e4d3e-0eae-4f78-940e-f17d0cb073d9" />

&nbsp;
3. In the Tags section, I selected **Add tag** and configured the following:
   - Key: Name
   - Value: My Snapshot
4. I selected **Create snapshot**.
5. In the left navigation pane, I selected **Snapshots** to view the created snapshot.
<img width="1602" height="380" alt="Screenshot 2026-04-05 183239" src="https://github.com/user-attachments/assets/ba91f579-1b2b-49da-b044-0d5f22a32636" />

The **Snapshot status** of my snapshot is _Pending_. After completion, the status changes to _Completed_. Only used storage blocks are copied to snapshots, so empty blocks do not use any snapshot storage space.

6. In the EC2 Instance Connect terminal window, I deleted the file that I had created on my volume by running the following command:
 - ```sudo rm /mnt/data-store/file.txt```

7. To verify that the file had been deleted, I ran the following command:
 - ```ls /mnt/data-store/file.txt```

8. I observed the following message:
 - ```ls: cannot access /mnt/data-store/file.txt: No such file or directory```
<img width="940" height="137" alt="image" src="https://github.com/user-attachments/assets/2162cae3-5953-4aa8-aa04-3307edef4d81" />

This confirmed that my file had been successfully deleted.

-----
_**Task 6: Restoring the Amazon EBS snapshot**_

In this task, I restored data stored in a snapshot by creating a new EBS volume from it.

**Task 6.1: Creating a volume using the snapshot**

1. On the EC2 Management Console, I selected **My Snapshot**.
2 From the Actions menu, I chose **Create volume from snapshot**.
<img width="1602" height="380" alt="Screenshot 2026-04-05 183239" src="https://github.com/user-attachments/assets/1c8c90d3-e682-4fa5-b719-ca8dbffcfbeb" />

&nbsp;
3. For Availability Zone, I selected the same Availability Zone that I had used earlier.
4. In the Tags (optional) section, I selected **Add tag** and configured the following:
   - Key: Name
   - Value: Restored Volume
5. I selected **Create volume**.
6. To view the new volume, I selected Volumes in the left navigation pane.

I observed that the volume status of my new volume was Available.
<img width="1592" height="343" alt="Screenshot 2026-04-05 183441" src="https://github.com/user-attachments/assets/e37a1eec-cb50-4454-b162-f1ae088eb83a" />

_I understand that when restoring a snapshot to a new volume, I can modify configurations such as the volume type, size, or Availability Zone._

**Task 6.2: Attaching the restored volume to the EC2 instance**

7. I selected **Restored Volume**.
8. From the **Actions** menu, I chose **Attach volume**.
<img width="1579" height="478" alt="Screenshot 2026-04-05 183522" src="https://github.com/user-attachments/assets/0bf7f2ed-b298-40e2-a8e0-84580b1ff58e" />

9. From the Instance dropdown list, I selected the **Lab instance**.
 - For the Device name field, I selected **/dev/sdc**, which I would use in a later task.
10. I selected **Attach volume**.
I observed that the volume status changed to **In-use**
<img width="1879" height="751" alt="Screenshot 2026-04-05 183544" src="https://github.com/user-attachments/assets/b7965589-87be-43e8-875b-29cb2caee756" />

**Task 6.3: Mounting the restored volume**

11. To create a directory for mounting the new storage volume, I ran the following command in the EC2 Instance Connect terminal:
- ```sudo mkdir /mnt/data-store2```
12. To mount the new volume, I ran the following command:
- ```sudo mount /dev/sdc /mnt/data-store2```
13. To verify that the mounted volume contained the file I had created earlier, I ran the following command:
- ```ls /mnt/data-store2/file.txt```

I observed that the **file.txt** file was present, confirming that the snapshot restoration was successful.
<img width="940" height="219" alt="image" src="https://github.com/user-attachments/assets/7075302c-0624-482c-8272-9dd6683b117f" />

---- 
**Conclusion**

I have successfully done the following:
- Created an EBS volume
- Attached and mounted an EBS volume to an EC2 instance
- Created a snapshot of an EBS volume
- Created an EBS volume from a snapshot

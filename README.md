# Ex--6-AWS-Account-setup-and-S3-creation-

## CLOUD STORAGE CREATION (S3) AND LAUNCHING AN (EC2) INSTANCE IN AWS
## NAME: UDHAYA PRAKASH V
## REG NO: 212224240177
## Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

## Algorithm / Steps
1.Create a new Amazon EBS volume with a size of 1 GiB.

2.Select the same Availability Zone as the EC2 instance.

3.Attach the EBS volume to the EC2 instance using /dev/sdb.

4.Connect to the EC2 instance using AWS Systems Manager Session Manager.

5.Check the available storage using df -h.

6.Create an ext3 file system on the EBS volume.

7.Create the /mnt/data-store directory.

8.Mount the EBS volume to /mnt/data-store.

9.Configure /etc/fstab for automatic mounting.

10.Verify that the EBS volume is successfully mounted.

11.Create file.txt inside the mounted EBS volume.

12.Verify the contents of the created file.

13.Create an EBS snapshot named My Snapshot.

14.Delete file.txt from the original EBS volume.

15.Create a new EBS volume from the snapshot.

16.Attach the restored volume to the EC2 instance using /dev/sdc.

17.Create the /mnt/data-store2 directory.

18.Mount the restored volume to /mnt/data-store2.

19.Verify that file.txt has been successfully restored.


## Program
## 1. Check Available Storage
```
df -h
```
## 2. Create an ext3 File System
```sudo mkfs -t ext3 /dev/sdb```
## 3. Create a Mount Directory
```sudo mkdir /mnt/data-store```
## 4. Mount the EBS Volume
```sudo mount /dev/sdb /mnt/data-store```
## 5. Configure Automatic Mounting
```echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab```
## 6. View the File System Configuration
```cat /etc/fstab```
## 7. Verify the Mounted Volume
```df -h```
## 8. Create a File in the EBS Volume
```sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"```
## 9. Read the File
```cat /mnt/data-store/file.txt```
## 10. Delete the File
```sudo rm /mnt/data-store/file.txt```
## 11. Verify File Deletion
```ls /mnt/data-store/```
## 12. Create a Mount Directory for the Restored Volume
```sudo mkdir /mnt/data-store2```
## 13. Mount the Restored EBS Volume
```sudo mount /dev/sdc /mnt/data-store2```
## 14. Verify Snapshot Restoration
```ls /mnt/data-store2/```

Expected output:

```file.txt```

## Outputs

<img width="1920" height="1200" alt="Screenshot (361)" src="https://github.com/user-attachments/assets/e55c0ada-6b2a-4681-ba42-f49de3141e41" />


<img width="1920" height="1200" alt="Screenshot (363)" src="https://github.com/user-attachments/assets/7739c1f4-e06b-4846-9c0e-4d954a86ff10" />


<img width="1920" height="1200" alt="Screenshot (364)" src="https://github.com/user-attachments/assets/090798ed-294f-419d-81fd-5c195df68cc6" />


<img width="1920" height="1200" alt="Screenshot (362)" src="https://github.com/user-attachments/assets/59516337-ef3b-4648-b62e-50c9529b41b3" />



<img width="1548" height="546" alt="image" src="https://github.com/user-attachments/assets/89ba01bb-35a1-4f41-bee6-94bed5f2021c" />

## Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.

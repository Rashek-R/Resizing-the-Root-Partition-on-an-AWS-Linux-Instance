# Resizing-the-Root-Partition-on-an-AWS-Linux-Instance
## The AWS elastic volumes allow online resizing of the volumes without any downtime of your applications. This is very useful for production applications. Here is the step-by-step tutorial to resize the EBS volume on the EC2 instance and grow the partition size.

Step 1: Go to the EC2 service in the AWS console and click on the server-specific volume by selecting the EC2 server > Storage > volume ID

![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/8dc4423c-4d2d-4634-9bbf-9b15ee522a25)

Step 2: Select the Volume > Actions > Modify volume

![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/5fef3e8a-621e-4905-9fc5-d78b412c37f7)

Step 3: Modify the volume size by changing the Size value > click Modify.

![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/23790e1d-bc32-47d0-9405-da2a65c3a970)

## Extending OS file system

After finish modifying the volume,need to extend the OS file system to increase volume size.

Step 4: SSH into the server and check whether the storage disk space is allocated by using “lsblk” command. increased volume will be shown just above current volume, e.g., xvda1 is current volume with 8GB size and  xvda with 10GB size

![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/b926f0d4-9f41-4934-b9c4-d00df6080668)

Step 5: Extend the partition by typing: sudo growpart /dev/xvda 1.  
Note: Here dev/xvda denotes the partition name and 1 denotes the partition number. 

![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/75cfe93a-273c-40d3-bbae-1f907ddc3885)

Step 6 : Extend the volume by typing: sudo xfs_growfs /dev/xvda1 

![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/444524c6-644e-4296-a4da-1a604e5c1993)

## Result
Now check the EBS size allocated to our server by using the “lsblk” command.
Hence, we have increased the EBS volume from 8GB to10GB

.![image](https://github.com/Rashek-R/Resizing-the-Root-Partition-on-an-AWS-Linux-Instance/assets/134732001/5d254192-0dd4-4896-afc2-1677449c285a)
 







#  Implementing web solution with Wordpress on a tier-3 architecture consisting of 3 different system instance to make up the 3 separate layers

## Task -- Implement a Client-Server Architecture using MySQL Database Management System that comprises of 3 separate layers namely:

- A Laptop or PC to serve as a client
- A CentOS EC2 Linux Server as a web server (This is where you will install WordPress)
- An CentOS EC2 Linux server as a database (DB) server

### Steps

1. Launching an EC2 instance to serve as the **Web Server** and creating 3 EBS volumes each of 10 GiB.

    ![Adding EBS volumes to EC2 instance](./images/adding-ebs-volumes.png)

2. Configuring the added EBS volumes in the Linux terminal

    ![Viewing partitions in EBS attached](./images/view-partitions-on--attached-EBS.png)

3. Creating single partitions on each of the attached EBS volume using the **gdisk** command. See partitions created below.

    ![Viewing created partitions in EBS attached](./images/view-partitions-on--attached-EBS.png)

4. Installing the logical volume package using `sudo yum install lvm2`

5. Checking for available disk partitions using -- `lvmdiskscan`

6. Uisng `pvcreate` to mark each of 3 EBS volumes attached as physical volumes (PVs) to be used by LVM

7. Adding EBS volumes to same volume groups using the *vgcreate** command as in -- `sudo vgcreate webdata-vg /dev/xvdh1 /dev/xvdg1 /dev/xvdf1`

8. Verifying physical volume group has been created using `sudo pvs` as seen below

    ![Viewing created physical volumes](./images/verifying-pvs.PNG)

8. Verifying volume group has been created using `sudo vgs` as seen below

    ![Viewing created partitions in EBS attached](./images/verifying-vg.PNG)

9. Verifying logical volume group has been created using `sudo lvs` as seen below

    ![Viewing created partitions in EBS attached](./images/)



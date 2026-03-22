# Working with Amazon EBS

## Lab Overview  
In this lab, I worked with Amazon EBS and learned how to create a volume, attach it to an EC2 instance, configure it in Linux, and use snapshots to back up and restore data.

---

## Creating the EBS volume  

I started by going to the EC2 console and opening the Volumes section.

![image](images/image1.png)

Then I created a new volume and added a tag.

![image](images/image2.png)

The volume was created successfully.

![image](images/image3.png)

I verified the volume details and configuration.

![image](images/image4.png)

---

## Attaching the volume to EC2  

Next, I selected the volume and attached it to the Lab instance.

![image](images/image5.png)

After attaching, I confirmed that the volume status changed to in-use.

![image](images/image6.png)

---

## Connecting to the instance  

I used EC2 Instance Connect to open the terminal.

![image](images/image7.png)

---

## Creating and configuring the file system  

I checked the existing storage using df -h, then created a file system on the new volume and mounted it.

![image](images/image8.png)

After mounting, I verified that the new storage was available.

![image](images/image9.png)

---

## Creating an Amazon EBS snapshot  

I created a snapshot from the volume.

![image](images/image10.png)

The snapshot was initially in pending state.

![image](images/image11.png)

After some time, the snapshot status changed to completed.

![image](images/image12.png)

---

## Restoring the snapshot  

I created a new volume from the snapshot.

![image](images/image13.png)

The restored volume was available and ready to use.

![image](images/image14.png)

I attached and mounted the restored volume and verified that the file was recovered.

![image](images/image15.png)

---

## Conclusion  

This lab helped me understand how EBS volumes work with EC2. I was able to create and attach storage, configure it in Linux, and use snapshots to back up and restore data when needed.

# Multi-Cloud Data Transfer with AWS and GCP


---

![Image](https://github.com/Alvin-Janton/Multi-Cloud-Data-Transfer/blob/9f8d7961ee15864b36c3e9eac9ce20270afa1274/images/architecture-annotated.png?raw=true)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use GCP Storage Transfer Service to transfer data from an S3 bucket to a GCP cloud storage. I'm doing this project to learn more about how cloud platforms store their data, and how to implement multi-cloud technologies.

### Tools and concepts

Services I used were AWS S3, IAM, Manifest files, GCP buckets, Storage Transfer Service. Key concepts I learnt include how to create a transfer job in GCP, how to transfer data from S3 to GCP, and how to use manifest files to transfer specific resources.

### Project reflection

This project took me approximately one hour and 15 minutes. The most challenging part was configuring the transfer job in GCP. It was most rewarding to see the files successfully transfer from S3 to the GCP bucket.

---

## Setting up Data in S3

I started this project by setting up an AWS S3 bucket. I then uploaded 3 files to that bucket to act as secure data.

![Image](http://learn.nextwork.org/intense_azure_festive_sow/uploads/aws-multicloud-storage_s1g7h8j9)

---

## Setting up GCP

Google Cloud Platform is a major cloud platform created by Google. It's used similar to AWS, where you pay for access to resources like compute, AI, storage and more. I set up a GCP account to create a storage bucket that I will connect with my S3 bucket.

GCP's free tier includes over 25 different services. I also get credit to spend on services that aren't avaliable in the free tier across the first 90 days of my account.

![Image](http://learn.nextwork.org/intense_azure_festive_sow/uploads/aws-multicloud-storage_s2g8h9j0)

---

## Storage Transfer

Data transfers are important for implementing multi-cloud solutions. Using multiple cloud providers for the transfer has benefits such as redundancy, cost, and infrastructure diversity.

The transfer is set up using Storage Transfer Service, which is a service that automates the transfer of data between cloud platforms. We need this service because doing data transfers manually would be slow, error prone, and expensive.

There are two different types of transfers you could set up, batch scheduling, and event-driven scheduling. The difference is, batch scheduling uploads all the data that is different from the previous backup, while event-driven scheduling uploads data any time a new object is stored.

![Image](http://learn.nextwork.org/intense_azure_festive_sow/uploads/aws-multicloud-storage_s3k2l3m4)

---

## Granting GCP Access to AWS

To connect AWS and GCP, I'm using identity federation, which works by granting GCP temporary access keys to my account to access resources. This is more secure than other methods because it ensures that only trusted entities have access to your account, and the access is temporary, so once GCP is done, it no longer has access until it makes its next request.

I created a custom IAM role for GCP because it does not have the permissions to access the bucket otherwise.

Within the IAM role, I needed to write a custom trust policy because there are no AWS native policies that allow for GCP to access your resources. The policy identifies GCS based on a subject ID, which is a unique credential related to your project.

![Image](http://learn.nextwork.org/intense_azure_festive_sow/uploads/aws-multicloud-storage_s4k3l4m5)

---

## Transferring from S3 to GCS!

To set up my destination GCS bucket, I needed to set up its region, which means the specific area where the data center is located. In this instance, I chose us-east1. Then I had to choose its storage class, which is the frequency in which the stored data will be accessed. Higher classes cost more, but are also faster to retrieve the data.

I verified my data transfer was successful by viewing the bucket that the data was supposed to transfer to. When I clicked into the bucket, I saw that the files had successfully transferred from S3 to GCP.

![Image](http://learn.nextwork.org/intense_azure_festive_sow/uploads/aws-multicloud-storage_s5k4l5m6)

---

## Transfer with a Manifest

In a project extension, I added more files to my S3 bucket, and I'm going to create a manifest file to transfer specific ones. A manifest file works by telling GCP the name of the file(s) to transfer.

I verified my data transfer was successful by viewing the bucket that the data was supposed to transfer to. When I clicked into the bucket, I saw that the files had successfully transferred from S3 to GCP.

![Image](http://learn.nextwork.org/intense_azure_festive_sow/uploads/aws-multicloud-storage_rththrthrth)

---

## Trial, Error, Success

---

---

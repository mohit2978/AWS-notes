# Lecture 48 2023 practical

RDS is regional

![alt text](image.png)

RDS dashboard you can see above!!

when we click on create DB!! 
we have 2 options!!
![alt text](image-1.png)

we use standard create as we need to select !! in easy create most of things are already selected!!

Then we select Engine type!! Suppose we select Postgrsql as free and opensource!!

When you create engine version , go and ask developer!! Which version he wants!!
As sometime s application might be compatible with certaain verion!!

Then we have templates!! we select free tier!! other are paid!! but lets see other options for producton!!
so lets select production just to see all version!!

Multi AZ is not enabled on Dev/Test and Free tier!!

Then 

![alt text](image-2.png)

## Amazon RDS deployment options
Amazon RDS supports three deployment options: single-AZ Instance, multi-AZ Instance, and multi-AZ DB Cluster. The availability of these options depends on the choice of the DB engine. We must know our workload and requirements to choose the right deployment option. In the following subsections, we’ll discuss all the available options and their usage.

### Single-AZ instance
In a Single-AZ instance deployment, Amazon RDS launches a DB instance within a single availability zone in the chosen region. All applications deployed in the same or different AZs within the region direct their read and write requests to this single DB instance. The diagram below illustrates how a Single-AZ instance deployment functions.

![alt text](image-3.png)

Since there is no secondary database instance, if the availability zone (AZ) hosting the primary DB instance becomes unavailable, all connected applications will experience downtime until the AZ is restored. In the event of a database instance failure, there will be no automatic failover. The recovery point objective (RPO) is typically around five minutes but can vary depending on the underlying architecture. However, the recovery time objective (RTO) can range from a few minutes to several hours.

>Note:Single-AZ instance is a good option for development and testing scenarios but not best for the production environment where high availability and automatic failover are required.

### Multi-AZ instance#
Multi-AZ instance deployment launches two DB instances in two different AZs. The first is called a primary instance, and the second is a standby instance. Like the Single-AZ instance, the primary instance entertains all the read and write operations, and the data is replicated synchronously to the secondary instance. The illustration below depicts the Multi-AZ instance deployment scenario:

![alt text](image-4.png)

In case of a failure, the failover process is initiated, promoting the secondary instance to the primary instance role. The failover process normally takes 1–2 minutes, and the RPO is zero because the data was backing up synchronously.

>Note:Multi-AZ instance is a good option for the production environment where High Availability and automatic failover are required. The secondary instance can’t be used for entertaining the read requests.

### Multi-AZ DB cluster
This deployment option creates a DB cluster with one primary instance and two readable instances in different AZs. Data is replicated from the primary to the readable standby instances in a semi-synchronized way that if any of the standby instances are acknowledged, the data change will be committed. The primary instance can take both read and write requests, but we can route all the read-only traffic to the standby instances to minimize the workload on the primary instance. The illustration below depicts the Multi-AZ cluster deployment scenario

![alt text](image-5.png)

When a failure occurs in this architecture, Amazon RDS automatically fails over to a reader DB instance in another AZ. The failover process normally takes up to 35 seconds, but it can take longer depending on the outstanding transactions of the failed writer instance.

>Note:Multi-AZ cluster deployment is only available for MySQL and PostgreSQL.

AWS manage all this things !! we need not manage all this

![alt text](image-6.png)

Then just identifier ,username and password!!

You can just put all your secreats in secret manager!!

![alt text](image-7.png)

Then instance configuration!!

![alt text](image-8.png)

Type of instance depends on application !! it is based on connections to the application!!

Then we have Storage!!
 
![alt text](image-9.png)

All database engines except Amazon Aurora use Amazon Elastic Block Storage (Amazon EBS) for data and log storage. Amazon Aurora uses shared cluster storage architecture. Amazon RDS has the following three types of storage for engines that support Amazon EBS:

1. General Purpose SSD -It is a cost-effective solution best suited for development and testing environments. The gp2 and gp3 are the most popular volumes of this type.

2. Provisioned IOPS SSD- This storage type is designed for I/O-intensive applications where consistent I/O throughput is required. This is best for production environments and optimized for online transaction processing (OLTP).

3. Magnetic- Amazon RDS uses magnetic storage to provide backward compatibility. 

>Note:It is recommended to always use General Purpose SSD or Provisioned IOPS SSD.

Now on storage , it will be based on discusion with developer how much storage we need!!

Provisioned IOPS -> max 80k we can give ,more IOPS more bill, more fast!!

![alt text](image-10.png)

We can have storage autoscaling ,if you think that your given storage will not be enough then use this!!

Then connectivity!! generally we connect to ec2 !!

![alt text](image-11.png)

If you do not select `connect to ec2` you can still connect by connection string!!

something Like

`jdbc:mysql://<hostname>:<port>/<database>?user=<username>&password=<password>`

If you select `connect to ec2` you can select ec2 instance where you want to connect!!

Network type : type of ip it will support , we choose ipv4 , dual stack means both ipv4 and ipv6

Never choose public access for DB!!

![alt text](image-12.png)

Then choose security group!! 

Then RDS proxy, just need to check the box!!It is billable!! just an extra layer of security!!






























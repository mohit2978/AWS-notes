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

we need to add inbound rules port number of ec2 and also that of db instance!!

![alt text](image-13.png)

Kerbros authentication means usage of active directory!! active directory stores username and password!!
We going with Password authentication!!

![alt text](image-14.png)

If you enable Devops guru it will give recommendations based on your usage!!

## Additional configuration

![alt text](image-15.png)

Inside engine what would be initial db name!! that we put in initial db name!!

![alt text](image-16.png)

Then on backup you see retention period which can be of max 35 days!! you can also select time at which
backup will take place!! You can choose option of chose a window!!

![alt text](image-17.png)

If Mumbai region goes down as a part of disastr management and recovery so we use backup replication!! 
this replication happens to another region automatically!!

>Note:If you need more than 35 days retention period use manual backup!!

![alt text](image-18.png)

If you select Log exports then logs will be send to cloudwatch!!


![alt text](image-19.png)

In mainatainenece we have enable minor update !! thn we can  choose a window!

Then we have delete protection which protects accidental deletes!!

![alt text](image-20.png)

Then we have monthly costs estimate!!

If your manager says reduce bil then!! You can do some optimization!! depending on load and everything!!


>Note: In free tier multiple options you see will be greyed out!!

AWS engineer not create table and writing scripts !! he just create databas engine!!

## Addons

![alt text](image-21.png)

Elastic cache is for incraseing performace!!

Cache we know what it is!!

RDS proxy we also know!!

these just add a lyer of cache and proxy just!!

![alt text](image-22.png)

When db is created it role is instance if you create read replica it will be chnaged to Primary!!

![alt text](image-23.png)

In actions you can see these options!!

Convert to Multi-AZ deployment!! if you add then it will double the charge!!


Quite easy to understand these options!!

When you create read replica it has same menu as we have while creating db instance!!
We can have max 5 read replica!!


Promte on read replica means promote to primary!!

Take snapshot means take manual backup!!

![alt text](image-24.png)

while restoring from snapshot we need to put a new name to db engine!!


>Note:creating db ,table ,query is devloper job not aws engineer job

Restore to pint in time:latest point in time restoration you will get restore not from snapshot!!

Migrate snapshot:Migrate one engine to other,just one click!!

![alt text](image-25.png)

>Note:RDS proxy is not supported for oracle

Whatever software you download download (latest-1 ) version!!!

On left you see Performace Insights  to see all performace issues!! 
here is session type you see idle connections that can be removed , that giving load to db and 
doing nothing!!

then snapshots you can see manaual snapshot!! and here you can restore!!

![alt text](image-26.png)

Upgrade snapshot to upgrade engine in snapshot!!
In on-premises it is big task!!

In on-premises you need to stop all connections take backup and then update new engine 
then restore all sb to that engine, huge task!!

To icrease memory , we need to chnage instance type so for that we need to stop and tis create downtime!!

Under system , you see all automatic snapshots!!


Reserve instance we can do for 1 or 3 years!!


You see parameter greoups, In Amazon RDS (Relational Database Service), a parameter group is a collection of configuration settings that define the behavior of a database engine. These settings influence various aspects of database performance and functionality, such as memory usage, timeouts, query optimization, logging, and more.


![alt text](image-27.png)


>Exporting any snapshot to s3 not all engine can be restored, while we restore from s3 ,Aurora and mysql can be restored

So PostgreSQL or any other can not be restored from s3!!


# EC2 continued

## Revision
Ec2 is regional as we know!!

In pricing model,in capacity estimation model ,we reserve capacity in a AZ.

## Storage Options

AWS offers flexible and easy-to-use data storage options for EC2 instances to meet all the requirements. Each option has its performance perks and cost. Some storage options offer persistent storage, while others provide fast temporary storage for the instance

### Elastic Block Store
Elastic Block Store (EBS) is a highly reliable, durable block-level storage volume that can be attached to the EC2 instances. Multiple EBS blocks can be attached to an instance. EBS storage attached to an instance after the launch can exist independently; however, the EBS volume attached by default while launching an instance is terminated with the instance. Default EBS volume can also be configured to exist independently. EBS offers different types of volumes based on different characteristics, such as gp2, gp3, io2 Block Express3, and io1. 

EBS offers backup through making point in times copies, also known as EBS snapshots. A snapshot in EBS is incremental, which means only the updated block is saved in the recent snapshot. The size of snapshots depends upon the size of the data backed up, and similarly, the cost of the snapshot is also based on the snapshot size rather than the volume size.

>EBS is a zonal service and can be attached to any instance in the same Availability zone. It is recommended for applications that require quick retrieval rates and continuous reads and writes.

### Instance store
An instance store is a temporary block storage for an instance physically attached to the host. Instance storage is also known as ephemeral storage. It is the fastest storage block available for EC2 since it is physically attached to the host, but not all the EC2 instance families support instance stores; for example C6 , and R6 EC2 families don’t support instance stores, while M5 EC2 instance family supports instance stores. Moreover, the instance store’s size depends upon the instance type. For example, m6id.large supports an instance of volume 1× 118 GB, and m1.small supports 1×160 GB.

![alt text](image.png)

An instance store can not be attached or detached once the instance is launched and only exists during the lifetime of the instance. It is important to note that no two instances can be attached to a single ephemeral storage. The instance store is ideal for temporary memory and cache, offering high read-and-write IOPS  and high-performance hardware.

### Amazon S3
An AWS S3 bucket is a scalable and durable object storage service that allows users to store and retrieve data from the internet. It provides a large storage and is designed for high availability and fault tolerance. S3 buckets can store various data types and specify access privileges according to the requirements.

### File storage 
EC2 instances are virtual servers in the cloud that can run applications and store data. File storage on EC2 instances involves creating, managing, and accessing files and directories within the storage attached to the instances. EC2 offers multiple file storage options to cater to different use cases and performance requirements, allowing one to choose the most suitable solution based on the application’s needs. Let’s take a look at the different file storage options available with EC2.
- Amazon FSx
    - Amazon FSx, a file storage service managed by AWS, simplifies the deployment and management of file systems. It provides two primary variations: Amazon FSx for Windows Server and Amazon FSx for Lustre. Amazon FSx for Windows File Server is a fully managed Windows file system with features such as high availability, data deduplication, and compatibility with AD. It streamlines file storage for Windows-based applications, including those hosted on Amazon EC2 instances, enhancing data reliability and accessibility.
- Amazon Elastic File System
    - The Amazon Elastic File System (EFS) is a user-friendly and scalable file storage solution that offers a dynamic adaptation of storage limits without impacting applications. This makes EFS an ideal choice for managing files without concerns related to server maintenance or storage capacity constraints. EFS allows simultaneous access by various EC2 instances across different AZs within the same region, facilitating a shared data source for applications operating on multiple servers.    

Lets see EBS(Elastic Block Store)
## EBS
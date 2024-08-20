## Overview Of services

Already seen load balancers and 5 services in Previous lecture

1. EC2
2. Elastic BeanStalk
3. lightsail
4. Lambda (serverless)
5. Event bridge
***
we create functions in lambda!!

Event bridge stores all events !!
***
Floppy-->2MB<br>
CD's-->700MB<br>
DVD's-->4.7GB <br>
Pen Drives-->128GB <br>
HDD-->2 TB<br>

These are not secure!! We need more storage!! so AWS comes up with service called as S3 (**Simple** **Storage** **Service**)

In Aws mostly services starting with Simple ends with Service e.g. service to send notification is SNS (Simple Notification service)! service to send Email SES (Simple Email Service)!

Google also has drive called google drive and AWS has S3!!
it is just a storage!

S3 is unlimited storage!can store  any kind of files!!
we say any kind of files as FLAT files!!

__Cannot execute any type of file in S3__<br>
__S3 is just storage__<br>
__S3 is serverless so we no need to think about High availability,scalability__
***
![alt text](image.png)
 
***
 Laptop <--> S3<br>
 Windows <--> none <br>
 Folder <--> Bucket<br>
 Files <--> Objects<br>
 KFG <--> Keys<br>

 S3 is object based storage!! Name of file is KEY!! Bucket is container of object!!

 __S3 is global but buckets are regional__

> **Note :** 
In case of static website, you can host on S3!! no need to go to EC2 or elastic beanStalk!! it does not support dynamic website hosting!!
 
 ***
 Now we see about EBS(__Elastic Block Storage__)

 Don't call Elastic BEanStalk as EBS ,EBS  full form is Elastic Block Storage!!

 S3 is object based storage but EBS is Block based storage!!
  It is like HDD!! you can run anything here!!

  here HDD is called as Volume (EBS Volume)! now we call HDD as Volume!!__When launching EC2 we need to tell Volume!! Ec2 comes with default volume called as root volume which has OS!!__ Rest of volumes is called as Additional volumes!! Anytime we can attach volume or detach it!!
  ***
  

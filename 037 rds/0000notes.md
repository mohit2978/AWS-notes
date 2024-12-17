# RDS 

This is from old lecture lec-47 and 48 of 2023 batch!!

In ec2 we call ec2 instance here we call it RDS db instance!!

We need to understand Read replica and Multi AZ!! Already seen in educative practical!!

Application read and write in DB!!

If you want to connect to DB In application we need hostname(End point):portnumber ,username and password!!

Every Db is connected via EndPoint!!

Here we cannot login like SSH as this is Platform as a service!! we can just connect to DB!!

There are some db which are read only!! for those application we create read replica so that whole load not comes to main DB!!

In primary DB we write and all read replica we read!! Every read replica has it own end point!!

Read replica can be in multiple regions !! for application in multiple regions!! All write on master server
and all read on replica !! all the write will be synched with replica after some time!! so after writes read will happen
asynchronously!!

Read replica is not for high availability it is just to __increase performance__!!

>Note: we can have max 5 read replicas

We can promote read replica to stand alone DB instance!!After promotion it is considered as normal instance !!
To make it primary we need to make it's read replica!!

## Multi AZ or Cluster

Group of DB instance is called as Cluster!! This is used for __high availability__!!

If you select Multi AZ ,one more Db instance will be created but we will not be able to see it!! it
will be managed by AWS!! here data replication will be synchronous between 2 Db's!!

>Note:If you enable Multi AZ you need to pay double the amount!!

if anything wrong happen to your db instance!! immediately failoover will happen to multi AZ DB instance
(Master sb be replaced by Multi AZ db instance)!!

>Note:here both the db instance have same endpoints!! so no effect on the application!! Also we will not be 
able to know if failoover happended or not!!

If someone deleted table failover will not happen, it happens when something wrong with whole DB!!

We can also enable Multi AZ for read replicas!!

You can reserve DB instances!!

## RDS features

Backups here is called as snapshot!!Backup of entire engine is snapshot!!

If backup of only 1 table , then this needs to be done by us only!! this is not managed by AWS!!

Patching/Updates of RDS handled by AWS!! 

We can also encrypt Databases!!can use KMS!!

To get performance we have performance insights!!

We have retention period (time for which backup is present max it can be 35 days) for Automatic backup !!

For manual backup there is no retention period .it will be there till you delete it!!

We can also export snapshot to s3!!





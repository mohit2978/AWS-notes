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

Read replica is not for high availability it is just to increase performance!!

>Note: we can have max 5 read replicas

































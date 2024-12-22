# Lecture 44 (Developer's topic)

Increase performace- ElasticCache

we know what cache is !! How it works!!

Application code need to be such that it find data in elasticcache first then go to RDS, Aws engineer not do that!! After getting data from RDs we put in cache!! Frequently accessed data is put in elastic cache!!

It is in memory DB caching service!!

ElasticCache supports two engine !! MemcacheD and Redis!!

Redis Supports High Availability ,Failover , Persistant data (stop and start redis ,data will be there),Backups whereas MemcacheD does not support any of these so people use Redis mostly!!

ElasticCache is mostly for read purpose!!

Basically whenevr you connect to server , You are in a session ,session data has all credentials ,ip adress etc which is stored in cookies , Elastic Cache can be used to store that data!!

>Note:It is Also  serverless! you can go with a server like choose instance type or be serverless based on traffic it will increase storage

![alt text](image.png)

## Lazy loading and write through difference

![alt text](image-2.png)

AWS Outposts is a fully managed service from Amazon Web Services (AWS) that extends AWS infrastructure, services, APIs, and tools to virtually any on-premises or edge location. It provides a hybrid cloud solution that allows you to run applications seamlessly across on-premises and AWS environments.

AWS Outposts is like bringing the AWS cloud into your own building. Imagine you have a piece of AWS sitting in your office or data center. It lets you use AWS services (like servers, storage, and databases) right where you need them, instead of only in the AWS cloud.

How It Works:
- Order It: Pick the setup you need, and AWS will deliver it to you.
- Set It Up: AWS will install the equipment at your location.
- Use It: You use AWS tools like normal, but now part of AWS is in your building.
- Relax: AWS keeps it updated and running smoothly.


Why Use It?
- For Low Latency: If your apps need super-fast responses or need to work with machines nearby, this helps.
- For Special Rules: If you have rules saying your data must stay in your country or building.
- For Local Work: If you want to process data nearby but still connect to the AWS cloud.

ElasticCache is service having 2 engine :redis and memcached like RDS is service having 6 engines!!

Redis is widely used so let us see that in detail!!

Cluster --> collection of shards!!

Shard --> collection of nodes!!In 1 shard there are 6 nodes!!1 Primary and 5 read replica!!

In 1 cluster you can have 500 shard!!


If no cluster mode then only one shrad if cluster mode enabled then can have 500 shrad!!

![alt text](image-1.png)

![alt text](image-3.png)

This elasticCache menu is very much similar to RDS!!

we choose to create MemcacheD

![alt text](image-4.png)

Easy create just everything is automatically selected and in Standard create we 
need to create everything!!

![alt text](image-5.png)


we choose standard create where we choose location as AWS cloud as on On premises cache will be sent to our location!!
That an outpost!!

![alt text](image-6.png)

see the above options we have selected!!Rest all same as RDS!!

>Note:To get max limits of any service see service Quotas Just select the 
service and you will get the Quotas

![alt text](image-7.png)

Adjustability means we can increase by raising the ticket to AWS!! If not adjustable it means we cannot increase it!!

>Note:ElasticCache is a key-value DB in backend!!

While Choosing redis you will get option to cluster mode enable or disable!!

![alt text](image-8.png)

If enabled it asks how many shrad and in every shrad how many max node you need!!

Redis supports backup and extra thing we have seen already than memcached!

![alt text](image-9.png)

Global datasource is just replication in another region!!

## Task

Connect redis cluster to Ec2!!





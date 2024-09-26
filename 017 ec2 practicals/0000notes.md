### Lec 27 ec2 practicals

instance meta data we get from details in managen=ment console!!

user data is bootstrap script which execute only once when ec2 machine starts!!

for attacks like DDos,we use AWS shield!!

## Practicals

We know ec2 is regional!!make sure you are in mumbai region as you are in India!! any service in AWS you use must be in Mumbai as closest to us!!

![alt text](image.png)

see all these concepts we already know in EC2 console!!

In AMI catalog you see the marketplace, there you can see all customized images!!

![alt text](image-1.png)

see QuickStart AMIs all are not free!! you need to select AWS free tier filter!!

![alt text](image-2.png)

we use redhat OS for now!! also we use x86 and 64 bit architecture!!

In marketplace we have every application!!you can get any application server on marketplace!!

![alt text](image-3.png)

Community AMIS are AMIS made by anyone !! so it is not recommended to use it !! use only verified one!!

in default security group we check only inbound rules!! in inbound rules by default everything is denied!!



![alt text](image-4.png)

in default security group you have one rule by default that allow all traffic to security group!! this rule says security group has whole access to the all traffic!! as we want security on all traffic so all traffic needed to be accessed by security group!! on src you see custom on right of that we have security group id!!

>never delete default rule!

sources custom ,anywhere ,myIP!! we use myIP!! once you select myIp aws automatically takes your ip!!

anywhere means anyone from world can access it !! if you select MyIP only you will be able to access it!!

![alt text](image-5.png)

To connect to windows machine we use RDP protocol!!

lets see placement group!!

![alt text](image-6.png)

lets create one

![alt text](image-7.png)

you can use it to group ec2 instance!!
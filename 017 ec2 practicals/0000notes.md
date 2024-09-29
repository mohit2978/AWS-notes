### Lec 27 ec2 practicals

instance meta data we get from details in management console!!

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

In marketplace we have every application!!you can get any application server on marketplace!!like you need jenkins then can see jenkins server where  jenkins will be already available!! if you don't know how to configure!!

![alt text](image-3.png)

Community AMIS are AMIS made by anyone !! so it is not recommended to use it !! use only verified one!!

in default security group we check only inbound rules!! in inbound rules by default everything is denied!!



![alt text](image-4.png)

in default security group you have one rule by default that allow all traffic to security group!! this rule says security group has whole access to the all traffic!! as we want security on all traffic so all traffic needed to be accessed by security group!! on src you see custom on right of that we have security group id!!

>never delete default rule!

id deleted default rule by mistake you can add it easily!!

sources custom ,anywhere ,myIP!! we use myIP!! once you select myIp aws automatically takes your ip!!

anywhere means anyone from world can access it !! if you select MyIP only you will be able to access it!!

![alt text](image-5.png)

To connect to windows machine we use RDP protocol!!

lets see placement group!!

![alt text](image-6.png)

lets create one

![alt text](image-7.png)

you can use it to group ec2 instance!!

cluster ,partition ,spread placement group we know!!
used to group ec2 instances!!

Network Interfaces on left on ec2 console!! it is NIC(network interface card)(the ip is assign dto NIC card)(if ip assigned then machine will have NIC card)(Aws will manage it) card!!

we know load balancers!!
you can see that too!!

we know target groups!!

we have Ec2 global view!!
it gets to see all ec2 regions in all regions!! used to see all machines in one place!!

you can see various resources running at various regions!! every region will have default vpc!! in vpc we have subnets!! and 1 default security group!!! all instances must be zero if no running!!

## Events on left side of ec2 dashboard!!

aws send notification here in form of events ki this host machine is in maiantainence!!

if something like maintenance is going on host machine and your ec2 goes down so it will be notified in events!!

>if you want to investigate you must go to cloudtrail!! it is service where everything is recorded!!

Look to events regularly!!here aws will send notifications!!



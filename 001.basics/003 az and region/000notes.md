## Region and AZs

Region is place where AWS has infrastructure!!
Region has multiple data centres!!
That data centre is called as AZs!!

Data centre==AZs
So servers are present in AZs!!

We have mumbai and hyderabad region!!

**Regions and Avalability Zones**
Region = Its a Geo-Graphical area , Ex AWS-Region = Mumbai
Availability Zone = Simply a DataCenter (AZ)

**Redundant AZs**
Ideally, you design your application to be across more than one AZ that way if one AZ goes down you have another.

When designing an application you try to have redundancy between the three AZs. That way if AZ1 goes down due to a power failure, AZ2 will be alive and will not be affected and in turn, your applications and their underlying data are not affected.

Every region has a code like mumbai has ap-south-1

![alt text](003_1.jpg) 
[screenshot: AWS Console region selector — US East (N. Virginia) us-east-1, US East (Ohio) us-east-2, US West (N. California) us-west-1, US West (Oregon) us-west-2, Asia Pacific (Mumbai) ap-south-1, Asia Pacific (Osaka) ap-northeast-3, Asia Pacific (Seoul) ap-northeast-2, Asia Pacific (Singapore) ap-southeast-1, Asia Pacific (Sydney) ap-southeast-2, Asia Pacific (Tokyo) ap-northeast-1, Canada (Central) ca-central-1, Europe (Frankfurt) eu-central-1]

See the codes above!! These are region!!
Ap→asia pacific

Mumbai has 3 AZs

Mumbai = ap-south-1
AZ's = ap-south-1a
       ap-south-1b
       ap-south-1c

To get Azs code just put a ,b,c at the end!!

Regions and Azs are managed byAWS!!

Now we launch 10 ec2 instances. Will we put all in one AZ or at multiple AZs?
If we put at 1 Azs,if that one Azs is down then we will not get response!!

![alt text](003_2.jpg) 
So we distribute!!
But all AZs are connected by internet !! so can launch few in one Az and other is some other Az
Suppose we are talking about mumbai region!! So 3 Azs

![AWS Region = Mumbai: a circle containing 3 Availability Zones (1a, 1b, 1c), each with 4 EC2 instances (green boxes), interconnected by red lines](svgs/003_3_mumbai_region_3az_ec2.svg)

Red line tells interconnected AZs
 Green boxes are ec2 instances!!

![alt text](003_3.jpg) 
**AWS has Global Infrastructure**
Region is a place where AWS has its Infrastructure
A Region contains multiple DataCenters
A Region contains multiple AZ's
    Servers = Instances
Servers / Instances are placed in AZ's
AZ's are sync with each other (network), not data
If required we can share the data to other AZ's in same Region.
Best practise is to distribute the EC2 instances across multiple AZ's

By default data will not be sync across multiple AZs you need to sync them !!
Till now ,there is no such time when Az goes down!!

1a is not a data center its a group of data center!!
So thats why AZ never goes down!

![1a / 1b / 1c labelled boxes listing the localities (dadar, andheri, aroli / juhu, thane, kalyan / kurla, church gate, dharavi) that make up each Availability Zone](svgs/003_4_az_group_of_dcs.svg)

A ec2 instance in 1a wil not be replicated to 1b or 1c!!

![alt text](003_4.jpg) 
**(recap)**
AZ's are sync with each other (network), not data
If required we can share the data to other AZ's in same Region.
Best practise is to distribute the EC2 instances across multiple AZ's
very very less chances that 1AZ goes down
1a or 1b or 1c = group of DC's
1 AZ is a group of DC's
Instances across AZ's can share the data if required as AZ's network are inter-connected with each other

Latency
1.high latency→ not wanted
2.low latency→we want (time need to load a website) (very low response time)

If customer from India set server in India only not in germany as germany servers will have high latency!!

![eu-west-1 region (Ireland / Another Region): a circle containing 4 Availability Zones (1a, 1b, 1c, 1d) fully cross-connected by green lines](svgs/003_5_ireland_region_4az.svg)

Now we have another region!!
Now Two Azs in a region can communicate with each other
But two regions cant communicate with each other!!
Mumbai region cant communicate with ireland by default!If required they can communicate!

![alt text](003_5.jpg) 
[image: combined recap slide — AWS Global Infrastructure bullets, Regions and Availability Zones definitions, Mumbai = ap-south-1 (AZ's ap-south-1a/b/c) with note "Regions and AZ's are managed by AWS" / "AZ's can communicate with each other by default" / "AZ's network are inter-connected", Low Latency = Good (0.0001 sec) vs High Latency = Bad (2 secs), "Regions dont communicate with each other by default if required yes"]

![AWS Region = Mumbai (3 AZs, red interconnects) and eu-west-1 / Ireland (4 AZs, green interconnects) shown side by side, joined by a dashed "Network — default ✗" arrow showing regions don't talk to each other by default](svgs/003_6_two_regions_no_default_link.svg)



### What is EC2?
This is a web service that provides a re-sizable compute in the cloud.

AWS EC2 reduces the time required to obtain and boot new server instances to minutes allowing you to quickly scale capacity, both up and down, as your computing requirements change.

In the old world if you need an app server or DB server, you would first need to talk to your developer, decide the size and number of cores you need, and then talk to your procurement team, and by the time the server is in your data center it could take 2+ months.

Now with EC2, you have this with a click of a button. This also means from a startup perspective you do not have the upfront cost of buying all the hardware you need.

EC2 changes the economics of computing by allowing you to pay only for the capacity that you actually use. You also have several tools at the disposal of the developers to build the applications to be resilient and isolate them from failure scenarios.

![alt text](003_6.jpg) 
![AWS reference architecture: Single Instance in Availability Zone (A), reached via laptop → DNS (left), vs a Redundant multi-AZ setup — laptop → DNS → DNS load balancer → 4 instances split across Availability Zone (A) and (B) → DNS → Master/Slave database with replication](svgs/003_7_single_vs_redundant_multiaz.svg)

Orange boxes are ec2 instances!! Exclamation mark tells its down!
Top one is having 1 ece so no redundancy so not highly available!

In down load balancer distributes traffic across multiple Az , 2 machines in Azs so yes highly available !!
 Load balancer is regional device!! It can distribute traffic across multiple  ec2-instances (servers) across Multiple Azs in region

A,B,C,D initialises some servers
Now we dont want different people  Ec2 instance to communicate with each other
So we need a private cloud so for that in which all ec2 instance of person can communicate but outside people cant!!
So we use VPC(virtual private cloud ) for that!!

![alt text](003_7.jpg) 
![Four VPCs (purple, blue, cyan, green circles), each containing 4 EC2 instances, all inside one big AWS circle](svgs/003_8_four_vpcs_with_ec2.svg)

Inner circles are VPC!!
Two Vpcs cant communicate with each other by default!
But if required can communicate!

You went to sulabh sauchalaya its public but in that we have private compartment thats like it!!

VPC is regional !! Vpc you can create for region!! At max you can have 5 VPC's!

![alt text](003_8.jpg) 
![Nested boxes: AWS > Region > VPC > AZ's > 2x EC2](svgs/003_9_nested_region_vpc_az_ec2.svg)

VPC is like private cloud ab poora aws thdi private kr doge islie we put limit of 5 max VPC's!

![alt text](003_9.jpg) 
![Three AZ boxes (1a, 1b, 1c) connected by red lines; a green VPC's EC2 instances and a blue/purple VPC's EC2 instances each span across all 3 AZ boxes](svgs/003_10_vpc_spanning_3az.svg)

See above green server are in one ec2 instance and purple one in another!! See vpc expands across Az's

![alt text](003_10.jpg) 
![AWS VPC reference diagram: Users → Internet Gateway → Elastic IPs → Public Subnet (Web Server Instance, DMZ 10.0.0.0/24) → Private Subnet (Relational Database, 10.0.3.0/24), all inside one Availability Zone, VPC 10.0.0.0/16](svgs/003_11_vpc_public_private_subnet.svg)

This is not Highly available as only one ec2 instance no redundancy !

![alt text](003_11.jpg)
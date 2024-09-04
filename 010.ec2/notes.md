# EC2(Elastic compute cloud)

Amazon Elastic Compute Cloud (EC2) offers resizable compute capacity(thats definition of elasticity and scalability) in the cloud. It allows users to run virtual servers, known as instances, for various computing tasks. EC2 offers a broad set of servers with the latest processors, storage, networking, operating systems, and different purchase models, including pay-as-you-go. EC2 is a secure, flexible, and scalable solution, enabling businesses to easily deploy, manage, and scale applications without investing in physical hardware.

> IAM is free Ec2 is free for 750 hrs per month!In month there is 720 hrs!!750 hrs is for all Ec2 instances not for single Ec2! Ec2 is billable for every hour!EC2 is pay as you go model!!

![alt text](image-1.png)

Ec2 is only charge for Running state!!

Suppose you launch ec2 for 5 min and terminate and one more instance you launched for 5 min and termminate,what will you pay?

suppose you go to internet cafe and use for 5 min ans he charge 20rs for 1 hour so will he charge for 5 min? no !! he will charge for 1 hour only so likewise here also AWS will charge for 1 hour!! whether you use it or not!

you started one machine started for 5 min so 1 hr usage and then 5 min then also 1 hr usage!! so total 2 hr !!

Suppose you created 5 Ec2 instances then you use each for 1 hour so now you will be charged for 5 hrs!!

![alt text](image.png)

> Ec2 is regional service

> We launch Ec2 never create Ec2 instance
## Amazon Machine Image (AMI)
An Amazon Machine Image is a pre-configured image provided by AWS that contains the necessary information required to launch an instance. AMI serves as a template for the root volume that includes information regarding the operating system, application server, and applications.

## Security Groups
 Security groups are like firewalls to the associated resources; they control the inbound and outbound traffic for an associated resource.

Security groups are used to secure EC2 instances from unwanted requests. We need to specify a security group to secure our EC2 instance whenever we launch an instance. If no security group is selected, EC2 uses the default security group of the VPC. The default security group has no inbound rules and allows all outbound traffic. 

### Security group rules
Security group rules control inbound and outbound traffic to the resource. These rules allow traffic filtering based on protocols, port numbers and IP addresses. Security group rules are always permissive, which means no port or protocol can be explicitly denied. The following rules control the incoming and outgoing traffic:

#### Inbound rules
Inbound rules are used to define incoming traffic to the associated resources.

- By default, all inbound traffic is denied.

- When multiple inbound rules apply to a traffic type, the rule with the most matching IP range, port, and protocol takes precedence.

- For example, common port numbers SSH (22) for secure remote access, HTTP (80) for web browsing, and FTP (20, 21) for file transfer allow traffic from anywhere IPv4 address (0.0.0.0/0).

#### Outbound rules 
Outbound rules define the outgoing traffic from the associated resource to the internet.

- All outgoing traffic from the associated resource is allowed by default.

- When different outbound rules apply to a specific traffic type, the rule with the most matching IP range, port, and protocol takes precedence.

When launching an EC2 instance, we can attach an existing security group or create a new one. We can also modify the existing security group and add new rules or remove some rules. We can also attach multiple security groups to an EC2 instance, where all the rules for each group are logically aggregated to create one set of rules. It helps to evaluate the traffic efficiently and properly.

---
#### Security group best practices#
- Least privilege principle: Adhere to the principle of least privilege, only allowing necessary traffic to and from instances.

- No deny rule: There is no explicit “deny” rule. If a rule is not explicitly allowed, it is denied by default.

- Separation of duties: Use different Security Groups for different purposes (e.g., web servers, database servers) to enhance security and management.



## Revision
1. Can a IAm user create another IAM user? yes if the user have IAM permission!!
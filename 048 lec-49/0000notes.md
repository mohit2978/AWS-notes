# lecture 49 VPC practical
## Steps
- create VPC 192.168.0.0/16
- create IGW and attach to vpc
- create public subnet 192.168.1.0/24
- create private subnet 192.168.2.0/24
- create NAt in public subnet and EIP is associated
- create public routing table and all taffic(0.0.0.0/0) of public subnet is routrd to IGW
- crate private routing table and all traffic in private subnet to NAT
- create new security group 
- launch baston server in public subnet
- launch private server in private subnet
- connet baston to private server

## Practical

let us see default VPC in Mumbai first!! As there no private subnet so no NAT!

>Note:when you create a new VPc, default security group ,NACL ,route table(main table) 
is created automatically!!

### Steps

- Create VPC ,Create VPC only not VPC and more as it will autoselect many things!!
- give name
- IPV4 manual input

    ![alt text](image.png)

- Tenancy default as on dedicated , dedicated bill will come
- click on create VPC

- Go to internet gateway and add tag and create it

![alt text](image-1.png)

- It will be in detached mode so go to Actions>Attach to VPC and select VPC you just created!

>Note: 1 IGW can be attached to 1 VPC

- Go to subnet and create subnet

>Note: 1 subnet attched to 1 AZ

![alt text](image-2.png)

Just like this create a private subnet!!

Now let us create NAT

![alt text](image-3.png)


- Create NAT put in public subnet, connectivity--> public and allocate elastic IP!!

![alt text](image-4.png)









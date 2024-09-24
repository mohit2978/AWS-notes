## Revision

Autoscaling (scale in scale out based on load)

>Dynamic scaling(scaling based on load) is recommended one

based on launch template (has steps to launch ec2 ),ASG will launch EC2! the application will be in AMI!!

based on requirement you can integrate SNS(Simple Notification Service)!!

then we learnt about load balancer!! 

network load balancer support static ip (1 static ip per AZ).

> we can't increase capacity on runtime !! we need to stop and then increase capacity by changing instance type!! in runtime only solution is ASG!! we increase capacity as when we have single Database server so if slow DB then we use scale up by changing instance type!!

# EC2 continued

### Types of Ip

1. public ip
2. private ip
3. elastic ip(EIP)
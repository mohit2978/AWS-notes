# Lecture 28 connect to ec2 instance

### Revision
in Advanced settings ,we have terminate protection if we enable it ,no one will be able to terminate our ec2 util the person disable the termination protection!!

## States of a instance

- when you launch its pending then it goes to running!!

- if you stop then two states stopping ,stopped

- if you terminate then shutting down then terminated!!

## status check

- system status check
- instance status check

both should be passed and managed by AWS!!


alarm concept is in cloudwatch!!

in Details you can see all instance metadata!!

- to get public ip we have to enable public ip while we are launching ec2 instance!! enable auto assign public ip!!

![alt text](image.png)

in Public IPV4 DNS you get host name !!here you see public ip in it!! now when you stop and start ec2 public ip changes so is public DNS!!

![alt text](image-1.png)

see when you stop ec2 you get to know for what you will be billed after stoping ec2 instance!! you will be charged for resources attached to ec2 instance!!
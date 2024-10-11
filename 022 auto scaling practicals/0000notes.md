# Lecture 32 notes

previously we launched two ec2 instances manually!! what happens if two ec2 instances goes down!! so we need to do auto scaling!!

see in extras 002 we have seen ASG(auto scaling group) .must see that!!

we use launch template of AMI which have application inside it!!

### let now see what we are going to do!!

we create load balancer and create empty target group!! ASG will do registration of ec2 instances of whatever it create!!

we tell ASG avg CPU utilization to 70 percent!!

we put desired capacity=4 so ASG launches 4 ec2 instances initially!! min=2 and max=6 we set up!!

ASG scale out scale in but we want notification whenever a machine goes down or up !! so we use SNS!!

in SNS we have two things 
1. topic
2. subscription

like youtube channel we have topic whenever someone put video in topic (channel) you will get notified if you have subscribed to his channel(topic)


you can subscribe via email or phone number (SMS)

-------------------------

example create a topic in 530PMbatch and all students who subscribe to topic will get notification !!

>SNS is push based system(sending notification)

------




































































# Lecture 33 Cloudwatch

ec2 was biggest topic and it is done!!

Cloudwatch is a monitoring service!!

Cloudwatch is all about 3 things:-

1. Alarms
2. events
3. Logs

> it watch all aws resources like s3 not only ec2!!

two types of monitoring
1. basic monitoring (every 5 min monitor)(free)
2. detailed monitoring (every 1 min monitor)(paid)


## Cloudwatch and ec2

we are seeing ec2 as completed ec2 but it can also monitor other services!!

cloud watch monitor some metrics called as host level matrices(which are only 4)!!
which is CPU,network ,disk ,status check!!

>Host level metrics does not have memory to monitor!! so cloudwatch 
do not monitor memory by default!!

so memory we need to configure !! so this is __Custom metrics__!!

![alt text](image.png)

---

### Alarms 

we tell cloudwatch to watch any metrics we want to monitor!!

we tell cloudwatch if cpu utilization >90 percent then we can get alarm!! we can even get notification
by SNS!!

you need to give threshold value here 90 percent is threshold value!!


mostly people use CPU metrics only!!

 you can also use other metrics accordingly!!

 
>If cpu utilization < 1 percent , then ec2 not in use!! then we can stop the ec2 instance!!
Alarms can do actions on ec2 instance like  stop ,reboot ,recover ,terminate!! recover means if 1/2 status check
or 0/2 alarm can recover !! but alarm can not start the machine again!!

Alarm has 3 states
1. ok (if cpu utilization is <90 percent)
2. In alarm (if cpu utilization > 90 percent)
3. Insufficient (if ec2 instance not sending any response to alarm)

Cloudwatch alarms are on single metrics ,we want to monitor multiple metrics to be sure!!

---

### Composite Alarm

 combination of alarms 

 when network utilization(high network traffic) is very high , then cpu utilization will be high!! 
 so we use two alarms here !! this is using 2 metrics so this is called as Composite alarm!!

Condition like OR and AND can be used !!

---





























































































# Practical Cloudwatch lec-34

Alarms can be created from ec2 console as well as cloudwatch console!! first launch ec2!!

![alt text](image.png)

you can create alarm here!!

or on selecting a ec2 server you see on row View Alarms!

on cpu utilization you see 5 min gap that is basic monitoring and you reduce the gap then it will be chargeable!!

On monitoring you see only metrics that is host level metrics! 95 percent we see CPU Utilization!!

if cpu utilization >90 then scale up else if cpu utilization< 10 scale down

![alt text](image-1.png)

to create an alarm click on + symbol on ec2 row when selected!! and then crete a alarm !!

Alarm notification put a topic of SNS!! select action!!

we put in 5 min if we get one time min cpu utilization<10 percent we get notification!!

![alt text](image-2.png)


### Lets see how to create alarm from cloudwatch!!

![alt text](image-3.png)

Click on all alarms and then click on Create Alarm!

![alt text](image-4.png)

>Note : To see a service is regional or global see that is you able to see regions from top right!! you able to select any region!!if yes then regional else global!!

first select Metric then select ec2 namespace (namespace :collection of metrics ) and then select Per-instance metrics as one ec2 instance!!

![alt text](image-5.png)

then search using instance ID!!
then you can select according to requirement what you want to do!!

> Note : we can put any number of alarm to any service!!

then we want to terminate ec2 so we go to ec2 actions!!

Other service will have different metrics but the process of creating alarm be same!!

To create composite alarm ,select ana alarm and then you can select multiple alarms!!

No ec2 actions for composite alarms!! you can write a script in lambda!!

>Note : Once ec2 stopped then alarm can not start it!

### Events

here we create rules , click on events it goes to event bridge!!

events like someone creates or terminate ec2 instance we get notification!

here we have event bus which has events !! we can share bus to other accounts too!! we using default one!!

we use event pattern !!

In AWS, EventBridge (formerly known as "CloudWatch Events") is essentially the AWS implementation of an event bus. It enables applications to respond to events from a variety of sources in a highly scalable, serverless manner. Here’s a quick breakdown of the concept:

1. Event-Driven Architecture
    - An event bus enables event-driven architecture by allowing different services or components to communicate through events. Events represent changes in state or updates, such as "order created" or "file uploaded."
    - AWS EventBridge allows AWS services, third-party SaaS applications, and custom applications to send and receive events, making it easy to build decoupled, event-driven systems.
2. How EventBridge Works
    - Event Sources: Events can come from AWS services, like S3 or EC2, or third-party SaaS services like Zendesk, Shopify, or custom applications.
    - Event Bus: EventBridge organizes these events on a bus, which can be thought of as a pipeline or stream of events.
    - Event Rules: Rules can be set up to match specific patterns or conditions in the events. These rules can route the events to various targets like AWS - Lambda functions, Step Functions, SQS queues, SNS topics, and more.
    - Targets: EventBridge can send these events to different targets for processing, enabling actions to be triggered based on specific events. For instance, an order creation event might trigger a Lambda function that processes the order.
3. Benefits of Using EventBridge as an Event Bus
    - Decoupling of Services: With an event bus, services can remain decoupled and unaware of each other’s implementations, allowing for greater flexibility and maintainability.
    - Scalability and Serverless: EventBridge is fully managed and serverless, allowing for automatic scaling and low-maintenance operation.
    - Integrated AWS Service Support: EventBridge can integrate with many AWS services, making it straightforward to create automated, event-driven workflows across AWS.
4. Use Cases for AWS EventBridge (Event Bus)
    - Real-Time Data Processing: Triggering data processing tasks as soon as new data is uploaded to S3.
    -  Application Integration: Integrating multiple applications (e.g., CRM, ERP) through events.
    - Automated Responses to Security Events: Responding automatically to security incidents detected by AWS services, such as unauthorized access attempts.
    - EventBridge essentially acts as AWS’s answer to an enterprise event bus, allowing easy coordination of event-driven applications across the cloud.

Then we use event source i.e. ec2 for us!! then we need to choose event type!!base on requirement choose event type!! choose state for which you want to get notified!!

can see steps on various site how to add events for a service!!

> Task : Create rule for get notification for launch of ec2

we click on events it will take us to eveent bridge!!

![alt text](image-6.png)

we have to create Rule!! i should recieve notification if someone stopped/started/terminated ec2 instance!!These type of things are done by event bridge!!

>You see EventBus it has events. we can share this bus to other accounts so that other account can also access this account events!!

1. Define rule detail

![alt text](image-7.png)

choose rule with event pattern as we define pattern

2. then next page we have to choose source so we choose ec2 so we choose firstly AWS events!!
On event pattern we choose Ec2!!

    Then we need to choose categories,based on requirement you need to choose categories!!we use __Ec2 instance state change notification__!! then select which state you want to get notification!!

3. then we have target we need notification so we choose target as SNS!! then all next and finish!!

now we want at 9pm ec2 should stop and 9 am it should start!! we use lambda in it!!

>Lambda has no permission to stop ec2 so here we use IAM role !! we should give ec2 inline policy permission not full permission to lambda so that lambda can only have access to stop and start of ec2!!

steps 
![alt text](image-8.png)

1. create ec2
2. create policy
3. create IAm rule for lambda
4. create lambda 
5. create rule for event schedule!!

>Volume if you leave it is billable in non-free tier, so if your free tier is over even volume will generate the bill!!

In free tier EBS volume is free !! After one year when free tier is over EBS volume is charged!!
For that you need to terminate the machine!!

There are some limits to lambda functions see:



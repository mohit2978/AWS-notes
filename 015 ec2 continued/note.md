### Revision
- 1 ec2 can have multiple Security group? yes
- NACL-->network access control list
- 1 subnet associated to 1 NACL
- 1 subnet to multiple NACL or AZ? no
- 1 NACL or AZ can have multiple subnet? yes


## Todays topic --> Autoscaling

Autoscaling scale out or in ec2 based on load!!

Horizontal scalability, sometimes called scaling out or in, adds more instances or nodes to a pool to handle increased load or remove from it. T

In AWS, services such as Amazon EC2 Auto Scaling and Elastic Load Balancing (ELB) practically take care of the horizontal scaling for users.

- Amazon EC2 Auto Scaling: This automatically adjusts the count of EC2 instances based on the application conditions so that performance levels are maintained. This service will help us make sure we have the right number of EC2s that are handling the load for the application, optimizing both cost and performance.

- Elastic Load Balancing (ELB): Automatically distributes incoming application or network traffic across multiple targets, such as Amazon EC2 instances, containers, and IP addresses, in multiple Availability Zones. ELB automatically scales the load balancer according to the traffic to the application that varies periodically, hence ensuring the traffic is even among all instances. This distribution optimizes resource use and maximizes application responsiveness.
### Auto Scaling Groups
> ASG is a service from AWS that helps the applications automatically adjust how many instances they use based on how much they need. Consider ASGs a smart system that watches over our application’s traffic, ensuring that it runs well. If more people start using our application and it gets really busy, ASGs will add more instances to handle everything smoothly. But when fewer people use it, ASGs take away some instances to reduce our operational cost.

Here are some important points regarding ASGs:

- ASGs automatically manage the collection of EC2 instances, adjusting the quantity in response to the demand to ensure that the application maintains optimal performance and cost-efficiency.

- ASGs can define the minimum, maximum and desired capacity that can be run to handle the workload, maintaining the desired capacity within this range.

- ASGs primarily focus on infrastructure management, ensuring instances are available to handle the application load.

### Benefits of using ASGs
Here are some benefits of ASGs:

- Cost efficiency: ASG does not have any cost, but we pay only for the resources we use, potentially saving substantial costs, especially for applications with variable loads.

- Increased availability: ASGs enhance our application’s availability and reduce failure risks by auto-scaling across multiple Availability Zones.

- Better resource management: ASGs eliminate the guesswork in capacity planning. We set the scaling policies, and ASGs handle the rest, ensuring our application receives the necessary resources without manual intervention.

- Flexibility: We gain precise control over instance configurations with launch templates, allowing for tailored scaling strategies.
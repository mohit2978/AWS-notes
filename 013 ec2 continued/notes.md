# EC2 continued lec-23

To encrypt snapshot we have KMS (key management service)!!

Data lifecycle manager(DLM) automates the process of taking snapshot!! you need to tell at which time to take snapshot !!Just to tell the rules of snapshot!

## Images
seen in previous lecture!!

whenever linux server use redhat as mostly used!!
when on windows use windows server!!

Company put there AMI with their software configured in Amazon marketplace !! you pay them and use their AMI's.

Image contains ,os can be in EBS or ISV! images also backed by either EBS or ISV!!

through DLM ,lambda's we can create AMI automatically!!

base AMIs we get ,we put software and create image of it!! if we get these AMIs automatically then these AMIs are called as Golden AMIs these are developed by EC2 image builder automatically!!
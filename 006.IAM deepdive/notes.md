# Lecture 16 IAM deepdive

![alt text](image-1.png)

IAM (idendiety and access management).with IAM you can control entire AWS resources centrally.

IAM is used for security purpose. It is security service
2 types of user
- root user(having all permissions/policies)
- IAM user(limited permissions/policies)

IAM is completely free an global!!

With IAM user ,with login to AWS console but not login to EC2 instance!!you create resources have separate credentials!!


Suppose we created following users
![alt text](image.png)

We can have multiple policies to single user ,attach and detach anytime!!

### Difference in Admin and root user
__Root user can see billing admin cant__

Never share root user and password to anyone always share the IAm user account!! to share your account create IAm user!!

For daily activity ,always use IAm user not root user!! as root user has full permissions!!

For security use google authenticator for Multi-factor authentication (MFA), MFA can be for both root user and IAM user!! As AWS admin ,its your responsibility to put MFA for every user (both root and IAM user)!!  for this use app called Google authenticator!!

### IAM Policies

IAM takes care of authentication and authorization. An IAM policy is a JSON document attached to the AWS resource that is used by the logged-in entity to authenticate itself or to the AWS resource to which secure access is required. This policy defines the scope of permission that the principal entity will have.

__To login to AWS we can also login via code ,CLI !! Fow windows you can use AWS console but then in AWs cosnole you need to install AWS CLI!!__

In cli there is only one command to launch EC2 but in console we have 7 steps!!
# Lecture 24

## Connecting to ec2
### Secure shell for Linux instances
Secure shell (SSH) is a cryptographic network protocol used for secure communication. It is commonly used to provide a secure and encrypted connection between a client and a server, allowing users to access and manage remote systems securely. SSH is widely used in various applications, including remote command-line access, file transfer, and tunneling.

![alt text](image.png)

#### Setup and connection steps
SSH requires a key pair to create a connection with the EC2 instance. A key pair consists of a public and a private key, a set of credentials to prove identity when connecting to an EC2 instance. We can divide the SSH connection into three major parts as follows.

- Key pair creation: When launching an EC2 instance, we can specify a key pair during the instance creation process. This key pair consists of a public key added to the EC2 instance and a private key securely downloaded to the local machine.

- Permission setting for private key: Ensure that the downloaded private key file has the correct permissions to be executed. For example, use chmod 400 to restrict access to the owner only.

- Connect using SSH:

    - Open a terminal on your local machine.

    - Use the ssh command to connect to the EC2 instance using the private key

 ``` bash
 ssh -i </path/to/private-key.pem> ec2-user@<instance-ip-address>

 ```   
Replace /path/to/private-key.pem with the path to your private key file, ec2-user with the appropriate user for the Linux distribution, and instance-ip-address with the public IP or DNS of your EC2 instance.

### Remote desktop for Windows instances
Remote Desktop Protocol (RDP), a network protocol offered by Microsoft, provides a graphical interface to connect to a Windows-based computer over a secure network connection. RDP allows users to interact with a remote desktop as if they were sitting in front of it, accessing its desktop environment, applications, and resources. It facilitates secure communication between remotely connected machines over an encrypted channel.

RDP is normally used in a client-server architecture; it operates on TCP and uses port 3389 by default. RDP offers secure remote access to Windows-based EC2 Instances.

### AWS Systems Manager Session Manager (Instance Connect)
AWS Session Manager allows to securely connect to the EC2 instances without managing SSH keys or opening inbound ports. It creates a temporary, secure session directly from the AWS console or CLI. It simplifies administration and improves security by eliminating the need for complex bastion hosts.

#### Setup and connection steps
- IAM Role configuration: Ensure that your EC2 instance has an AWS Identity and Access Management (IAM) role with the necessary permissions for Systems Manager.

- Session Manager installation: AWS Systems Manager Agent (SSM Agent) must be installed and running on the EC2 instance. Most Amazon Machine Images (AMIs) come with SSM Agent pre-installed.

- Systems Manager Console connection: In the AWS Management Console, navigate to Systems Manager, go to “Session Manager,” and select “Start Session” for the desired EC2 instance.

- Browser-based SSH or Remote Desktop access: Use the browser-based AWS Management Console to securely access your EC2 instance without the need for external SSH keys or Remote Desktop client software.

#### Best practices for secured connection
- Security groups: Ensure that the security group associated with your EC2 instances only allows incoming traffic on the relevant ports, 22 for SSH and TCP 3389 for Remote Desktop.

- Key pair management: Keep your private key files secure and rotate them periodically for enhanced security.

## 
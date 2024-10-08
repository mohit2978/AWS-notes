![alt text](image-15.png)

AWS’s provision of Content Delivery Networks (CDNs) refers to its offering of services like Amazon CloudFront and Global Accelerator, which are designed to distribute content across a network of servers located around the world. This setup helps in reducing latency by serving content from a location nearest to the user. AWS’s CDN services are highlighted as solutions to enhance content delivery speed and reliability, enabling businesses to efficiently reach their global audience by overcoming geographical limitations and improving the user experience through faster content loading times.

1. Why Combine S3 and CloudFront?
- Scalability: S3’s virtually unlimited storage meets CloudFront’s robust CDN network.
- Performance: With CloudFront’s global edge locations, content is served from the nearest location, reducing latency.
- Security: Control access, integrate with AWS WAF, and deliver content over HTTPS.

## Steps
- Step 1 - Signup and get an AWS account. 
- Step 2 - Make sure you can access S3 and cloudfront (this will automatically happen if you are the root user of that account)

![alt text](image.png)


This approach will not work for frameworks that use Server side rendering (like Next.js)
This will work for basic React apps, HTML/CSS/JS apps

build react project on local

```bash
npm i -g serve
serve
```

- Step 3 - What are CDNs?

A CDN stands for Content Delivery Network. 
As the name suggests, it’s an optimal way for you to deliver content (mp4 files, jpgs and even HTML/CSS/JS files) to your users.

It is better than serving it from a VM/EC2 instances because of a few reasons - 

![alt text](image-1.png)

![alt text](image-2.png)

- Step 4 - Creating an object store in AWS

You can create a bucket in there. A bucket represents a logical place where you store all the files of a certain project.

- Step 5 - Upload the file bundle to S3

- Step 6 - Try accessing the website

![alt text](image-3.png)

- Step 7 - Connecting Cloudfront
    - Step 1 - Create cloudfront distribution
Go to cloudfront and create a new distribution. A distribution here means you’re creating a place from where content can be distributed.

    - Step 2 - Select your S3 bucket as the source

    ![alt text](image-4.png)

    ![alt text](image-5.png)

    
> Origin Access Control (OAC) is a feature in Cloudfront, which allows you to restrict direct access to the content stored in your origin, such as an Amazon S3 bucket or a web server, ensuring that users can only access the content through the CDN distribution and not by directly accessing the origin URL.


By the end of this, you should have a working cloudfront URL.
![alt text](image-6.png)

- Step 8 - Connect your own domain to it
    1. Select edit on the root page
    ![alt text](image-7.png)

    2. Attach domain name
    ![alt text](image-8.png)

    3. create certificate
    ![alt text](image-9.png)

    4. Follow steps to create the certificate in the certificate manager

    ![alt text](image-10.png)

    ![alt text](image-11.png)

    5.  Add a CNAME record for the website to point to your cloudfront URL

    That’s it, you have a fully running react project hosted on HTTPS on a custom domain
- Step 9 - Error pages    
![alt text](image-12.png)
![alt text](image-13.png)

![alt text](image-14.png)

week 22 aws

links 

1.https://medium.com/geekculture/deploy-a-static-website-using-aws-s3-and-cloudfront-55cfdbea1f4

2.https://medium.com/@nikola.kuzmic945/deploy-a-static-website-on-custom-domain-using-aws-s3-cloudfront-85a4983c1fe5
# Lecture 46 Route53

Route53 is DNS service,53 is DNS port number ,it is all about route, nasty URl we chnage to a beautiful url!!

DNS keeps track of hostname and IP!! and converts one another to each other!!

>Route53,Cloudfront,s3,IAM is Global

DNS is all about records!!

In route53 we create hostedzone!!

Route 53 is a scalable Domain Name System (DNS) service. The “53” in Route 53 refers to the TCP and UDP port number 53, a standard port for DNS services. However, before diving into the concepts of Route 53, let's briefly review how DNS works.

## What is DNS?
Every device connected to the internet has its unique IP address, enabling communication with it. When we browse the internet, we access web applications hosted on servers, each identified by a distinct IP address. For instance, consider the case of educative.io. If we assume that the content of educative.io is stored on a server with the IP address 104.18.2.119, then educative.io is a domain name that directs users to this server. We can access the same content using the educative.io domain name or the server’s IP address.

Let’s explore how DNS resolves the domain request for educative.io. Here, we will assume that the TLD server responds with the address of the authoritative server responsible for educative.io.

- Resolver and Root DNS: The client domain requests are forwarded to the DNS resolver. The DNS resolver then forwards the requests to the root server, and the root server responds with the TLD server address.

    ![alt text](image.png)
- Resolver and TLD name server: The DNS resolver forwards the client request to that TLD server. The TLD server interprets the request and responds with the address of the responsible authoritative server.

    ![alt text](image-1.png)
- Resolver and authoritative server: The DNS resolver receives the response from the TLD server and forwards the request to the responsible authoritative server. The authoritative server contains the Resource records and zone files for each domain. The authoritative server resolves the query and responds to the DNS resolver with the educative.io server’s IP address.

    ![alt text](image-2.png)

- Response to the user: The DNS resolver provides the client with the response and stores this response in its cache memory for any possible requests that it might receive in the future. The user connects to the server to access educative.io.

    ![alt text](image-3.png)

## Route53 features
1. it can provide domains like godaddy etc
2. can do domain registration ,DNS routing
3. Health check
4. Routing policies

When you create hosted zone ,hosted zone name should be same as domain name like if domain name is boom.com then hostedZone name is boom.com!!

We create record in hostezone where we map our domainName to nastyURL!!

So when request comes to route53 , route53 routes the request from boom.com to nastyurl!!

HostedZone is container of records!!

## What is Route 53?
Route 53 collaborates with top-level domain registries such as .com, .io, .net, and .org. When a domain is registered using Route 53, it first checks with the registry for that top-level domain if it is available. Route 53 then automatically makes itself the DNS service for the domain by doing the following:

1. Route 53 creates a hosted zone with the same name as the domain.

2. Route 53 allocates a set of four name servers to the newly created hosted zone. When users attempt to access the registered domain through their web browsers, these name servers direct the browser to the appropriate resources, such as a web server or other services.

3. Route 53 retrieves the name servers associated with the hosted zone and links them with the registered domain to ensure seamless DNS resolution.

4. As the registration process concludes, Route 53 forwards the domain information to the registrar responsible for managing domain registrations. 

5. The registrar then forwards the domain information to the corresponding registry, which maintains a database of domain registrations for specific top-level domains, such as .com. Additionally, certain details may be included in the public WHOIS database for transparency and accessibility.








































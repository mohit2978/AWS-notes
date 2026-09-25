## Architecture

Client is one who requests a resource. Server is the one which responds to the request of resource.

![Client Server Architecture](svgs/001_1a_client_server_architecture.svg)

Both should be in the same network!! Each device either hub/switch can be either client or server!!
 If it is requesting then client if fulfilling the request then server!!

Types of architecture!!

1 tier→ you develop your code on local !! no one else can access it!! Db on the computer also !!

This is one tier As your laptop is acting as client as well as server!!
Not good to keep client and server in the same machine!!

2 tier → Logic and db in server!!
 UI in different machine!!

![2-Tier Architecture](svgs/001_1b_2tier_architecture.svg)

---

If memory issues Application and DB taking too much space then server might crash !!
Like tatkal ticket in railways!!
So it is not good to keep Application And DB in the same machine!!
No need to worry about the client layer!!
No 2-tier architecture in prd env(real time)!!
Customer connecting to server ! That server is called as prd environment!

**Some of the advantages of the two-tier client/server structure are:**
- This structure is quite easy to maintain and modify.
- The communication between the client and server in the form of request response messages is quite fast.

**Disadvantages of Two - Tier Client/Server Structure**
- If the client nodes are increased beyond capacity in the structure, then the server is not able to handle the request overflow and performance of the system degrades.

To test code before going to prd code is tested in Test Environment!!
After test we have pre-prd environment!! Pre-prd is similar to prd!!

![Dev's Mobile -> PROD Environment -> Pre-Prod -> Test Environment -> devgun developer flow](svgs/001_2_dev_prod_preprod_test_flow.svg)

2 tier disadv is application and db in same env so memory issues so we separate them out and thats how we get to 3 tier!!

3 tier→

![alt text](001_2.jpg) 
Application server where application is hosted !!

![3-Tier Architecture](svgs/001_3_3tier_architecture.svg)

IP is unique identifier of computer in network!! Like aadhar card is the unique id of person in country!!
Your application server must be in private network as we dont want everyone to see code!!
But client in public network!! How client will access application server!!

So we use web server!It just takes  request from client and redirect to application server!! Her we don't have any code!!So the Application server is always a private network!!


N tier(microservices)

====================================
DNS
====================================

![alt text](001_3.jpg) 
![DNS resolution flow (root/TLD/authoritative/local DNS, TCP+SSL handshake, load balancer) into Server A and Server B (WebServer/Application Server/Database)](svgs/001_4_dns_resolution_and_servers.svg)

You access google.com .
Google.com is the hostname!! But browser understand IP

[meme image: "ONE DOES NOT SIMPLY ... REMEMBER EVERY WEBSITES IP ADDRESS" - imgflip.com]

![alt text](001_4.jpg) 
**Steps to resolving a domain name**
1. Web browser and OS will first check whether the domain is in their cache. If yes, done
2. The web browser then will send a request to a DNS resolver. A DNS resolver is a local server with a central database of DNS nameservers. This DNS resolver will be hosted with your ISP
3. The resolver will first check its cache. If the IP address for google.com isn't in its cache it will forward the query recursively up the to the root servers,
4. Down to the Top Level Domain (TLD) of google.com( .com would be the TLD in this case), and then down to the authoritative name servers responsible for www.google.com.

DNS system is organized in an upside down tree-like structure right?
We will go to the top and search downward. First stop is the root servers.
Root servers respond with address to the .com Top-Level Domain(TLD). Top-level domain just refers to the last chunk of a domain name after the dot symbol. Here we go to the .com TLD.
The resolver then queries .com servers for the authoritative name servers of our domain, google.com

- Authoritative name servers will respond with the corresponding IP address of www.google.com
- But first, it will save this IP to its cache. Caching every step of the way!
- The user's operating system will also cache this IP address for reference in the future—in case you want to visit this website again

DNS is like a distributed map <Hostname,ip address>

Cache is called as local DNS!!

![alt text](001_5.jpg) 
![Root Name Server flow from Srinivas's Laptop / Browser via Local DNS](svgs/001_6a_root_name_server_laptop.svg)

RootNameServer checks the domain whether its .com or .uk or whatever!!
Here its .com so root name server goes to .com top level domain!!
Google is hostname and .com is top level domain so for now we go to .com top level domain

![Top Level Domain (.com/.org/.in) identified by Root Name Server (RNS)](svgs/001_6b_top_level_domain_arrows.svg)

Here root name server sends to .com top level domain!!

![alt text](001_6.jpg) 
![Srinivas Request path through Local DNS, RNS, TLD to the set of .com domains (google.com among many)](svgs/001_7_srinivas_request_and_com_domains.svg)

So now among itn e sare .com we need to find google.com!!

There will be a person called name server who tells come here,here is google  !!
Ist name sever who identifies hostname

And then its directs us to SOA where we get IP

**What is a DNS SOA record?**
The DNS 'start of authority' (SOA) record stores important information about a domain or zone such as the email address of the administrator, when the domain was last updated, and how long the server should wait between refreshes. All DNS zones need an SOA record in order to conform to IETF standards.

![alt text](001_7.jpg) 
![Full DNS lookup flow: Name Server/SOA, Top Level Domain, Root Name Server (RNS), Local DNS, Browser on Srinivas's Laptop](svgs/001_8_full_dns_lookup_flow.svg)

Now we got the ip address!!
To get google page now we can go to google server by ip

Now there server we have a firewall !! which allows some sender ip and disallow sender ip !!
Basically it has allow and disallow rules!!

![alt text](001_8.jpg) 
![DNS lookup flow with data packets going through the Network into the Firewall (Allow/Deny Rule) at Google Company](svgs/001_9a_dns_lookup_plus_firewall.svg)

Here on the firewall we put rules like disallow http  and allow https !!

![Default protocol port numbers: http = 80, https = 443, SSH = 22, RDP = 3389](svgs/001_9b_protocol_port_table.svg)

Imp protocol port number!!
Http not secure connection to website!!
Https secure connection to website!!
SSH used to connect to linux machines!!
RDP used to connect windows machines!!

## Firewall stops unauthorized access to the network!!!

Now on google request 1st go to web server and then to app server and then to db server!!

![alt text](001_9.jpg) 
![Firewall with a 3x3 grid of WebServer, App Server, DB Server inside Google Company](svgs/001_10a_firewall_grid_9_servers.svg)

Now the request goes to which web server has multiple web servers!!

![Three Application Servers with IPs 192.168.10.20, .21, .22 (Shashank's URLs)](svgs/001_10b_three_application_servers_ips.svg)

Shashank need domain name not 3 ips !!  so for that we have load balancer which have name as hostname!!

![alt text](001_10.jpg) 
![DNS Name / Load Balancer distributing http://shash.com traffic to 3 Application Servers](svgs/001_11_load_balancer_to_app_servers.svg)

## Load balancer distributes the traffic to multiple servers!!
Follow the round robin method!!

Google request after firewall goes to load balancer!! Load balancer is exposed to public!!
Name of the load balancer is the domain name!!

![alt text](001_11.jpg) 
![Firewall + Load Balancer + 3x3 grid of WebServer/App Server/DB Server at Google Company](svgs/001_12a_firewall_lb_grid_9_servers.svg)

If the website is not working you can check in the firewall,load balancer  and then servers!!

## DNS DONE !! NOW HTTP
The user's web browser can now follow HTTP(HyperText Transport Protocol) and send a GET request to the server at google.com's

![HTTP GET request/response flow between Client (Browser), HTTP over TCP/IP, and Server](svgs/001_12b_http_get_request_flow.svg)

![alt text](001_12.jpg) 
**HTTP**
- HTTP is the protocol used to transfer data to and from the website.
- WWW is the identifier that indicates that it is a web site and it uses the HTTP protocol.
- HTTP://anything.com, WWW.anything.com, HTTP://WWW.anything.com leads to the same site.

Remember http protocol has default port no 80 not 8080

[image: "http://google.com" with syntax "Protocol :// DomainName:Port" (Port highlighted)]

Above you can see the syntax of the url but we never put the port number for any url!!
## Why are we not put port number?
For http if we put 80 or not its equivalent!!as 80 is default port number for http!!
For customers always use the default port number so no need to put it we can deduce from protocol used!!

[screenshot: Chrome address bar showing "https://google.com:443" being typed, with autocomplete suggestion "Google - https://google.com"]

See both url in above pic is same!! If we put any other port number it will not giv any output

![alt text](001_13.jpg) 
[screenshot: Chrome error page "This site can't be reached" for https://google.com:143/ — "The webpage at https://google.com:143/ might be temporarily down or it may have moved permanently to a new web address." ERR_UNSAFE_PORT]

As default port number is 443 for https
No customer is interested in remembering port number so we use default port number!!

HTTP = HyperText Transfer Protocol          http://google.com
HTTP Default port  number is 80              Protocol :// DomainName:Port
For Customer it should be always 80 or 443

![Application server (tomcat, port 8080) at 192.168.10.20, reachable via :8080](svgs/001_14_tomcat_8080_app_server.svg)

Tomcat running on 8080 2nd ip is correct one to access above pic server !! but is that ip we can give to customer!!
 1st and last ip is same as http default port number is 80
But we know we have load balancer

 See below wrong way for giving url to customer

![alt text](001_14.jpg) 
![Load balancer forwarding http://boom.com:8080 (wrong way) to 3 App 8080 servers](svgs/001_15a_lb_to_app_8080_ports.svg)

 Load balancer will map port 80 to 8080
So will give url to boom only with http protocol which says port 80 now load balancer change the port to 8080 and while coming back change the port to 80

![Load balancer converting incoming port 80 to 8080 for the App servers, and back to 80 on the way out](svgs/001_15b_lb_port_mapping_80_to_8080.svg)

Inside server you can have any port number, but load balancer uses default port number which is exposed outside!!

![alt text](001_15.jpg) 
You can customize the port number at application level but at load balancer it's always the default port number!!

Http  transfers the data from client to server and vice versa in the form of hypertext!!
Http is basically a format in which we are sending data !!

![HTTP request headers example (POST request) split into Request headers, General headers, Representation headers](svgs/001_16_http_request_headers_table.svg)

**HTTP response status codes**
HTTP response status codes indicate whether a specific HTTP request has been successfully completed. Responses are grouped in five classes:
1. Informational responses (100 – 199)
2. Successful responses (200 – 299)
3. Redirection messages (300 – 399)
4. Client error responses (400 – 499)
5. Server error responses (500 – 599)

![alt text](001_16.jpg) 
**HTTP Status Code**
404 = Page not Found
500 = internal server error
503 = Service Unavailable

500 ⇒ internal service is down!!
200⇒ page found/success
503⇒server down!!

Disadv of http→ not secure!!

You put the credit card number ,cvv  now http take it to network and network is very dark!!
Http have all the info in clear text!!

![HTTP data packet (Src, Dest, Protocol, Port, Data, Secure: NOT — Plain Text/Clear Text) intercepted by a Hacker](svgs/001_17_http_data_packet_hacker.svg)

## So we use https!! Here we have all the info in encrypted format!!
Always check you are using https!!

![alt text](001_17.jpg) 
[screenshot: Chrome "Security" panel for google.com — "Connection is secure. Your information (for example, passwords or credit card numbers) is private when it is sent to this site. Learn more" and "Certificate is valid" with tooltip "Show certificate (issued by GTS CA 1C3)"]

This certificate we get from godaddy!!
This is called an ssl certificate or https certificate!!

Https is all about certificates!!

Tomcat is an application server engine x is a web server!!

## Http Over TCP/IP
TCP connects two servers by 3 way handshake!!
On top of it http/https all protocol works !!
TCP is like a bridge and http/https packets are people!!

![alt text](001_18.jpg) 
![HTTP over TCP/IP: Server 1 (HOST, IP) connected to Server 2 (HOST, IP) via TCP](svgs/001_19a_server1_tcp_server2.svg)

 Or can call TCP as track and packets as metro!!

We have UDP which is not reliable!!
UDP→user datagram protocol!

![7 Layers of the OSI Model: Application, Presentation, Session, Transport, Network, Data Link, Physical](svgs/001_19b_osi_7_layers_table.svg)

![alt text](001_19.jpg) 
Lets see the OSI layer!!
A boy needs to communicate with a girl on bus stop!! Don't ever say HI to a girl!!

Dont say you are beautiful !! she will tell me something new!!

1. To communicate 1st both need to be physically present!!(PHYSICAL)
2. Now both communicate by mouth in data we communicate by data link!!
3. Both should in same bus stop so both in same network!!

![Boy (HOST 1) and Girl (HOST 2) in the same Network - physical layer](svgs/001_20a_boy_girl_physical_layer.svg)

     4.we tell a friend go and talk to girl for me and he establish connection between you and girl here friend is TCP for connection establishment!!
     If UDP friend he is not trusted he might take your girl!!

![Boy (HOST 1) and Girl (HOST 2) connected via TCP](svgs/001_20b_boy_girl_tcp_connection.svg)

![alt text](001_20.jpg) 
     5.connection is established by friend now we dont need friend we can have private session with girl!! (Session layer)
     6.present to girl (Presentation )
     7.Application ( go to movie etc)

**Analogy of picking up cookies from grandma's house**
1. IP would be the road on which we drive
2. TCP would be the car
3. And HTTP would be the box of cookies moving from one location to another

![Application/Transport/Internet/Network-Link layers as road (IP), car (TCP), box of cookies (HTTP) moving from Client to Server/grandma's house](svgs/001_21a_osi_cookies_grandma_analogy.svg)

**SSL (HTTPS)**
- Client say Hello
- Server says Hello(do you have cer[tificate])
- Client generated symmetric key
- Server verify the key
- Once verification is successful
- Secure data transfer

![SSL (HTTPS) handshake flow between Client and Server: request, certificate answer, verification, key generation, client identification, verification/encryption of symmetric key, symmetric encryption/secure data transfer](svgs/001_21b_ssl_https_handshake_flow.svg)

![alt text](001_21.jpg) 
**Load Balancer, WebServer, Application Server and Database**
1. Load Balancer: The job of a load balancer is to.... balance loads.
2. WebServers: Web servers supply the web content for web browsers; what the browser requests, the web server delivers through Internet network connections.
3. Application servers host and execute applications and can be used to communicate and extract data from a database
4. Da (rest of this line is crossed out by a hand-drawn line in the original image)

![Load Balancer/WebServer/Application Server/Database numbered flow: Client → App server → Database and back](svgs/001_22_lb_webserver_appserver_database_flow.svg)

![alt text](001_22.jpg)
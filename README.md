
This is a repository where i show you what i learned about subnetting doing the last project of my course titled "comunicación de datos" at Universidad de Lima. In this project I used Cisco Packet Tracer to implement the routing plan, the dns server, protocols such as FTP, TELNET and dynamic routing (DCHP). 

## IMPORTANT CONCEPTS

I consider important to review concepts before showing you how i implemented them, so the following is a table of contents with all the concepts used in this project.

* Routing
* Static Routing
* Dynamic Routing
* Domain Name System (DNS)
* File Transfer Protocol (FTP)
* Dynamic Host Configuration Protocol (DHCP)
* Teletype Network (TELNET)
  

## ROUTING

Routing is the process where we search to find the most optimal way of connecting all the nodes of a network, so we can reduce waiting times and unexpected blocks. Additionally, finding the optimal route allows us to scale the topology more easily. There are two types of routing: static and dynamic. In static routing, the IP address and subnet mask are set manually by the network administrator, while in dynamic routing, the IP address and masks are set up automatically by the routers according to the network conditions.

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/8d268c4e-8ae3-477f-8f1e-a1eac4eea3e7)
Note: This is an example of a network set up using static routing, as you can see it's a simple network which doesnt have many devices


## STATIC ROUTING

In static routing, as was mentioned before, is the network administrator who is in charge of setting which are the IP adress for each router and final device. These type of routing is used in less complex topologies because it's easier to configure and also because there aren't many devices which needs an ip address. Another advantage of using static routing is the it requires less computational resources because unlike dynamic routing where part of the cpu processor capacity has to be used for determining which are the ip addresses for each device, in static routing the ip address this is not neccesary because the these are put by the same administrator who knows that these ip address can not change with the time unlike the dynamic routing.


## DYNAMIC ROUTING

Dynamic routing proves highly advantageous for network scalability, particularly when authorities anticipate an increase in network size over time. By employing protocols such as DHCP (Dynamic Host Configuration Protocol), authorities can swiftly allocate new IP addresses to emerging devices. DHCP, defined as **"a network protocol that automatically assigns IP addresses and other communication parameters to devices connected to a network" (Gillis, 2023)**, streamlines the process, ensuring efficient network expansion.

### HOW DHCP WORKS? 

Think of the DHCP server like a hotel front desk. It keeps a bunch of IP addresses, kinda like rooms in a hotel. When a new device joins the network and asks for an IP address, the DHCP server gives it one from its pool, just like how a receptionist hands out room keys to guests when they check in. It's like finding a free spot in the hotel to stay, making sure everyone gets connected easily.

These can be better visualized in the next figure:

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/3b65b980-906b-47d9-b44e-bfc063586d5c)

As you can see, the client has to ask for an ip address to the DHCP Server who give it a IP address as a response and it's the client who confirms if it will use that IP address. It's important to mention that generally in the mid term of the conception period the client must renew the ip conception sending a DHCPREQUEST to the current DHCP to keep the ip address until the end of the period and when the device will be removed from the network it has to send a DHCPRELEASE request to the DHCP Server so the IP address can be released.

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/aaac927e-6e13-4cb6-a322-8c90474a06f8)


## DOMAIN NAME SYSTEM (DNS)

A Domain Name System is a system which allows to relate ip addresses to domain names so the users can connect to the devices without having to memorize the ip address of each one. When we enter to www.google.com we use the domain name instead of the google-server ip address because it's easier to remember the domain name instead of the ip address, but internally is the DNS who is in charge of translating the domain name in the ip address of the server which we want to connect to. Before explaining how the DNS works turns out important to explain the types of DNS firstly. There are two main kinds of systems, the resolver/recurrent and the authoritive DNS, the first is often provided to the user by its Internet Provider and it's the one which has to be communicating with others servers to be able to determine the ip address of the wanted server. On the other hand, the autoritive DNS it's the direct provider of the ip address, it's the one who has the wanted ip address in its ips-table.

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/d088f658-aca2-42bd-a695-657a165c3e19)

In the diagram above, the DNS resolver is depicted searching for the domain name by reaching out to name servers to identify which one holds the corresponding IP address in its pool. Initially, the resolver contacts the DNS root name server to pinpoint the server responsible for .com domains. Subsequently, it queries the .com Name Server to locate the server hosting domains related to www.example. Finally, the resolver communicates with that server to determine the IP address of the www.example.com domain. Once found, the DNS resolver furnishes the IP address to the end user, enabling it to directly communicate with the www.example.com server. To expedite future communication between www.example.com and the end user, the server's address is cached within the DNS server. This cache ensures quicker access to the IP address for subsequent requests.

## FILE TRANSFER PROTOCOL (FTP)

The File Tranfer Protocol allows the communication between two devices so they can share files as .txt, videos, images and others. For a securer communication is important that the users who will connect to the servers must have limited permissions so they won't have unlimited access. 

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/66969bf9-cb59-4774-a696-d2a9fad82399)


## TELETYPE NETWORK (TELNET)

The TELNET protocol allows the user to enter into another TCP/IP network computer from  its own device to be able to control it. It enables users to establish a command-line interface (CLI) session with a remote host, allowing them to execute commands, manage files, and interact with applications as if they were directly connected to the system. Nowadays, this protocol has been supplanted by more secure protocols as SSH (Secure Shell).

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/012d89ac-c1de-4e6f-a579-7c7d16f8a866)


## PROJECT STATEMENT


![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/36c31899-5434-4c35-9359-ca73c8164f35)

The project has the next instructions:

1- Design (First deliverable): Based on the shown topology, you must create the addressing plan for ACME company, considering that the company has been assigned the IP network 179.62.0.0/17. The central Headquarters consists of three buildings (SC1, SC2, SC3), and it's connected to five branches (one building per branch) with different host requirements as indicated in the topology. You must include in your addressing plan the WAN links between the central headquarters and the branches.

2- Implementation (Second deliverable): The designed addressing plan must be implemented using Cisco software: Packet Tracer. Select both communication equipment and end devices, as well as suitable tranmission media, accurately. It is suggested that the router at the central headquarters is the DCE (Data Communication Equipment) and the other fives are the DTE (Data Terminal Equipment). As total connectivity is required, it's suggested to use static routes to achieve this communication scenario between branches.


## IMPLEMENTATION

### Finding the subnetting mask
  Making a sum of all the hosts required to connect we can see that in total is 1580 hosts while the network mask is /17 which allow us to have 32768 hosts. As we can the difference is a lot so we need to reduce the number of hosts     
  because there are many host ip address that won't be used, so we determined that a subnetting mask of /21 will give us 2048 hosts (2**11) which meets the requirement of 1580 hosts. So the new subnetting mask will be /11 and its from     this point where we'll start to find the ip address for each branch and central server.

  *New subnetting mask: 255.255.248.0*

### Making the subnetting tree
  We put each branch and central server its subnetting mask 
  
  ![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/a179cdec-d65d-45fe-89f2-d1420eb432b4)

### Assining IP address and mask to each one

  ![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/924bdfff-c81f-4bdf-a074-3692a7084962)

### To put IP Address to each SC we use the following command


```
!SC

configure terminal

interface  f 0/0

ip address 179.62.0.1 255.255.254.0

no shutdown

interface  f 0/1

ip address 179.62.2.1 255.255.255.0

no shutdown

interface  f 1/0
ip address 179.62.3.1 255.255.255.128

no shutdown

interface s 0/0/0

ip address 179.62.7.129 255.255.255.252

clock rate 64000
bandwidth 15000
no shutdown

interface s 0/0/1

ip address 179.62.7.133 255.255.255.252

clock rate 64000
bandwidth 15000
no shutdown

interface s 0/1/0

ip address 179.62.7.137 255.255.255.252

clock rate 64000
bandwidth 10000
no shutdown

interface s 0/1/1

ip address 179.62.7.141 255.255.255.252

clock rate 64000
bandwidth 10000
no shutdown

interface s 0/2/0

ip address 179.62.7.145 255.255.255.252

clock rate 64000
bandwidth 10000
no shutdown

end

wr

```

### Connect los switchers a los routers and the routers to the SC 

```
!S1

configure terminal

interface f 0/0

ip address 179.62.4.1 255.255.255.0

no shutdown


interface s 0/0/0

ip address 179.62.7.130 255.255.255.252

no shutdown

end

```

### Making the routing between SC and each router so they can have a bidirectional communication

```
!S1>>SC
configure terminal 
ip route 0.0.0.0 0.0.0.0 s 0/0/0
end
```

### Putting telnet to each router

```
!clave telnet
configure terminal
line vty 0 4
password grupo6
login
enable secret grupo6
end
```


### Connecting through ftp protocol code

```
!ftp
ftp 179.62.0.2
Users: admin/user
password: ulima/ulima
```


### Setting up a DNS Server

1- Set the ip address for the DNS Server

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/be71088c-ff06-4fab-8bd2-9727ffd8e53a)


2- In the services we can set up the DNS service and defining which is the Name Server (the ip of the dns address) and the Arecord which are the domains and its IP address, for example www.admin.com will be related to 179.62.0.2 which is SC1

![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/deccf1ee-e9ab-4f1e-b1c9-bd1ab741a54c)

## Final Result

  ![image](https://github.com/adrielardiles/Subnetting-Exercise/assets/120150352/895b5e23-e421-495b-9599-b1bf0bf63438)

We can use the TELNET and FTP protocol and we have a DNS Server which saved the domain name for SC1, SC2 and SC3






















## BIBLIOGRAPHY

- Amazon Web Services. (2023, Retrieved March 17). ¿Qué es DNS? – Introducción a DNS. Retrieved from https://aws.amazon.com/es/route53/what-is-dns/

- Gillis, A. S. (2023). DHCP (Dynamic Host Configuration Protocol). TechTarget Recovered from https://www.techtarget.com/searchnetworking/definition/DHCP




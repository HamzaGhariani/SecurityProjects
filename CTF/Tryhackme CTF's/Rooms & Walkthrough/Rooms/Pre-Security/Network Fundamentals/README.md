# [Network Fundamentals](https://tryhackme.com/room/whatisnetworking)
Networks are simply things connected. For example, your friendship circle: you are all connected because of similar interests, hobbies, skills and sorts.

Networks can be found in all walks of life:

    A city's public transportation system
    Infrastructure such as the national power grid for electricity
    Meeting and greeting your neighbours
    Postal systems for sending letters and parcels

But more specifically, in computing, networking is the same idea, just dispersed to technological devices. Take your phone as an example; the reason that you have it is to access things. We'll cover how these devices communicate with each other and the rules that follow.

In computing, a network can be formed by anywhere from 2 devices to billions. These devices include everything from your laptop and phone to security cameras, traffic lights and even farming!

Networks are integrated into our everyday life. Be it gathering data for the weather, delivering electricity to homes or even determining who has the right of way at a road. Because networks are so embedded in the modern-day, networking is an essential concept to grasp in cybersecurity.

Take the diagram below as an example, Alice, Bob and Jim have formed their network! We'll come onto this a bit later on.

![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-networking/d1v1.png)
> Hamza , 28/2/2022

------------------

## PART 1 :

- What is the key term for devices that are connected together?

`Network`


![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-networking/what-is-the-internet/internet2.png)

**private network**

**public network**

- Who invented the World Wide Web?

`Tim Berners-Lee`

- What does the term "IP" stand for?

`Internet Protocol`

- What is each section of an IP address called?

`octet`

- How many sections (in digits) does an IP address have? 

`4`

- What does the term "MAC" stand for?

`Media Access Control`

- What protocol does ping use?

`ICMP`

- What is the syntax to ping 10.10.10.10?

```bash
ping 10.10.10.10
```

- What flag do you get when you ping 8.8.8.8?

```bash
ping 8.8.8.8
```

-------------------------

## PART 2 :

Local Area Network (LAN) Topologies

**Star Topology**

![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-lan/star.png)

**Bus Topology**

![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-lan/bus.png)

**Ring Topology**

![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-lan/ring.png)


- What does LAN stand for?

`Local Area Network`

- What is the verb given to the job that Routers perform?

`Routing`

- What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?

`Switch`

- What topology is cost-efficient to set up?

`Bus Topology`

- What topology is expensive to set up and maintain?

`Star Topology`

- What is the technical term for dividing a network up into smaller pieces?

`Subnetting`

- How many bits are in a subnet mask?

`32`

- What is the range of a section (octet) of a subnet mask?

`0-255`

- What address is used to identify the start of a network?

`Network Address`

- What address is used to identify devices within a network?

`Host Address`

-What is the name used to identify the device responsible for sending data to another network?

`Default Gateway`

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/b27c024d90342c60dd5cb35765e7ed7b.png)

- What does ARP stand for?

`Address Resolution Protocol`

- What category of ARP Packet asks a device whether or not it has a specific IP address?

`Request`

- What address is used as a physical identifier for a device on a network?

`MAC Address`

- What address is used as a logical identifier for a device on a network?

`IP Address`

![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-networking/what-is-a-network/DHCP.png)


- What type of DHCP packet is used by a device to retrieve an IP address?

`DHCP Discover`


- What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?

`DHCP Request`

- Finally, what is the last DHCP packet that is sent to a device from a DHCP server?

`DHCP ACK`


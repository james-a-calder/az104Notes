# AZ-104 - Day 2 (Networking)
## Administrate Virtual Networks
Networking Layers (OSI (Open Systems Interconnection) Model)
- Application
- Presentation
- Session
- Transport (TCP/UDP)
  - TCP: Connection oriented, works on handshakes and making sure everything sent was received.
  - UDP: Connectionless, just send
- Network
  - IP
  - ARP: Address Resolution Protocol (find MAC from IP)
- Data Link
  - Switches
  - Bridges
- Physical
  - Hubs
  - Repeaters
  - Modems
  - Cables
  - etc...

Way to remember the layers from bottom to top: **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way

NAT - Network Address Translation

Public IP > NAT > Private IP

3 ranges of IPs that are not globally routable:
10.0.0.0
172.16.0.0
192.168.0.0

APIPA (Automatic Private IP Addressing) when no DHCP server exists ranges normally 169.255.0.0

DNS
Gateway
Subnet Mask
IP

3 Network Classes subnet
255.0.0.0 - A
255.255.0.0 - B
255.255.255.0 - C

CIDR - Classless Inter-Domain Routing

The Five IPv4 Classes
- Class A - For networks with a large number of total hosts. Class A allows for 126 Networks by using the first octet for the network ID The first bit in the octet is always zero. The remaining seven bits in this octet complete the network ID. The 24 bits in the remeaining three octets represnt the host ID and allows for approx 17 million hosts per network. Class A network numbers begin at 1 and end in 127.
  - Public IP Range: 1.0.0.0 to 127.0.0.0
    - First octet value range from 1 to 127
  - Private IP Range: 10.0.0.0 to 10.255.255.255 (See Private IP Addresses below for more information)
  - Subnet Mask: 255.0.0.0 (8 bits)
  - Number of Networks: 126
  - Number of Hosts per Network: 16,777,214
- Class B addresses are for medium to large sized networks. Class B allows for 16,384 networks by using the first two octets for the network ID. The first two bits in the first octet are always 1 0. The remaining six bits, together with the second octet, complete the network ID. The 16 bits in the third and fourth octet represent host ID and allows for approximately 65,000 hosts per network. Class B network number values begin at 128 and end at 191.
  - Public IP Range: 128.0.0.0 to 191.255.0.0
    - First octet value range from 128 to 191
  - Private IP Range: 172.16.0.0 to 172.31.255.255 (See Private IP Addresses below for more information)
  - Subnet Mask: 255.255.0.0 (16 bits)
  - Number of Networks: 16,382
  - Number of Hosts per Network: 65,534
- Class C addresses are used in small local area networks (LANs). Class C allows for approximately 2 million networks by using the first three octets for the network ID. In a class C IP address, the first three bits of the first octet are always 1 1 0. And the remaining 21 bits of first three octets complete the network ID. The last octet (8 bits) represent the host ID and allows for 254 hosts per network. Class C network number values begins at 192 and end at 223.
  - Public IP Range: 192.0.0.0 to 223.255.255.0
    - First octet value range from 192 to 223
  - Private IP Range: 192.168.0.0 to 192.168.255.255 (See Private IP Addresses below for more information)
  - Special IP Range: 127.0.0.1 to 127.255.255.255 (See Special IP Addresses below for more information)
  - Subnet Mask: 255.255.255.0 (24 bits)
  - Number of Networks: 2,097,150
  - Number of Hosts per Network: 254
- Class D IP addresses are not allocated to hosts and are used for multicasting. Multicasting allows a single host to send a single stream of data to thousands of hosts across the Internet at the same time. It is often used for audio and video streaming, such as IP-based cable TV networks. Another example is the delivery of real-time stock market data from one source to many brokerage companies.
  - Range: 224.0.0.0 to 239.255.255.255
    - First octet value range from 224 to 239
  - Number of Networks: N/A
  - Number of Hosts per Network: Multicasting
- Class E IP addresses are not allocated to hosts and are not available for general use. These are reserved for research purposes.
  - Range: 240.0.0.0 to 255.255.255.255
    - First octet value range from 240 to 255
  - Number of Networks: N/A
  - Number of Hosts per Network: Research/Reserved/Experimental

**Private IP Addresses**

Within each network class, there are designated IP address that is reserved specifically for private/internal use only. This IP address cannot be used on Internet-facing devices as that are non-routable. For example, web servers and FTP servers must use non-private IP addresses. However, within your own home or business network, private IP addresses are assigned to your devices (such as workstations, printers, and file servers).

- Class A Private Range: 10.0.0.0 to 10.255.255.255
- Class B Private APIPA Range: 169.254.0.0 to 169.254.255.255
  - Automatic Private IP Addressing (APIPA) is a feature with Microsoft Windows-based computers to automatically assign itself an IP address within this range if a Dynamic Host Configuration Protocol (DHCP) server is not available on the network. A DHCP server is a network device that is responsible for assigning IP addresses to devices on the network.
  <br/><br/>
  At your home, your Internet modem or router likely provides this functionality. In your work place, a Microsoft Windows Server, a network firewall, or some other specialized network device likely provides this functionality for the computer at your work environment.
- Class B Private Range: 172.16.0.0 to 172.31.255.255
- Class C Private Range: 192.168.0.0 to 192.168.255.255

- https://www.meridianoutpost.com/resources/articles/IP-classes.php

PAT - Port Address Translation

https://www.rfc-editor.org/rfc/rfc1918 - This document specifies an Internet Best Current Practices for the Internet Community

**IPs with /n after them - CIDR (Classless Inter-Domain Routing)**
The"/16" notation at the end of an IP address is part of something called CIDR (Classless Inter-Domain Routing) notation, which is used to specify IP addresses and their associated network masks. Here's what it means in a simple way:

IP Address: The part before the "/". This represents the address of a device or network. For example, in "192.168.1.0/16", "192.168.1.0" is the IP address.

/16: The part after the "/". This tells you how many bits of the IP address are used for the network portion. In this case, "16" means the first 16 bits of the IP address are the network part.

To break it down:

An IP address is made up of 32 bits (in IPv4).

The "/16" means that the first 16 bits are reserved for the network address, leaving the remaining 16 bits for device (or host) addresses within that network.

In simpler terms, "/16" means you have a very large network, capable of hosting up to 65,536 (2^16) devices.

https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide Office 365 IP Ranges

Categories
Optimise - Most Important (High Priority)
Allow
Default

**NAT Support with Office 365**
https://learn.microsoft.com/en-us/microsoft-365/enterprise/nat-support-with-microsoft-365?view=o365-worldwide 

To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).

Use the following formula to calculate the number of supported devices per IP address:

Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)

For example, if the following were true:

Restricted ports: 4,000 for the operating system

Peak port consumption: 6 per device

Peak factor: 4

Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000

Recommendation is to not exceed 2,000 devices

DHCP - Dynamic Host Configuration Protocol

DORA
- Discover
- Offer
- Request
- Acknowledge

Machine: I have no IP
Machine Broadcast: Discover - 'I need a IP address'
DHCP Broadcast: Offer - 'I have this IP for you if you'd like it?'
Machine Broadcast: Request - 'Yes please, I will take address x.x.x.x'
DHCP Broadcast: 'Sure, you can have it'

Typically this lasts 8 days before a renewal is required

Q: Why do we have subnets?
A: Used to segment networks, think house address within street address so you don't have to scan the entire network to find things close.

NIC - Network Interface Card

## Plan Virtual Networks
- Logical representation of your network
- Create a dedicated private cloud-only virtual network
- Securely extend your datacentre with virtual networks
- Enable hybrid cloud scenarios

You can not connect a VM to more than 1 Virtual network (you can connect to two subnets within a single vNet)

If you assign a machine an ip address and then remove the resource that IP address will **not** be reused until all other unused ranges have been taken.

On Prem you can ip-release ip-renew to pick up changes in the cloud this is **not** possible. you will have to reboot the machine.

The recommendation is  that you should never assign public IP to a as it would be open to the world. 

BAAS???

**Creating a public IP address as a resource**
- Available in IPv4 or IPv6
- **IP SKUs**
  - Basic: By default it is open with no protection. It doesn't offer any redundancy.
  - Standard: Traffic is blocked by default and is zone redundant.
- Dynamic vs Static
  - Static: Same IP address all the time
  - Dynamic: When resource is deallocated the ip address is released and a new when assigned when allocated.
- Availability Zone (Standard Only)
  - Tier:
    - Global
    - Regional
- Routing preference
  - Microsoft: If everything is within our vNet.
  - Internet: If we have users that need to connect from the outside world (the Internet) 

**Associate Public IP Addresses**
Insert table In Network8


Load ballance Network Layer 4
App Gateway Network Layer 7

Stopped vs Deallocated
- Stopped: Machine is shutdown from within the VM `Start > Shutdown`. All linked resources for the VM will remain allocated and you will pay for them.
- Stopped (Deallocated): Stopped from within Azure. All linked resources are also deallocated which means you no longer pay for them (if using pay as you go).

**Implementing Network Security Groups (NSG)**
- Limits network traffic to resources in a virtual network
- Lists the security rules that allow or deny inbound or outbound network traffic:
  - Inbound security rules
  - Outbound security rules
  - Rules have a priority lowest goes first
- Associated to a subnet or a network interface
- Can be associated multiple times

In the Networking tab of the VM creation we can chose to link our existing NSG t the the VM via the advanced option

***Questions will form a how many NSgs or what is the minimum number of NSGs required to fix X***
You need the number of NSGs to match the number of unique rule combinations that exist.
If everything within the subnet uses one ruleset then 1 NSG at subnet level is fine. **Note that you can use application security groups for extra granularity within a NSG**

**Determine**

**Create NSG rules**
- Source: (Any, IP Address, My IP Addresses, Service tags and application security group)
- Destination: (Any, IP Address, My IP Addresses, Service tags and application security group)
- Service (HTTPS, SSH, RDP, DNS, POP3, Custom, etc...)
- Priority: Unique, lowest number is highest priority, 100 is the lowest

**Implement Application Security Groups**
Allows you to group resources into a collection/service/application

- Extends your applications structure
- ASGs logically group virtual machines - Web servers, application servers
- Define rules to control the traffic flow
- Wrap the ASG with an NSG for added security

**Determine Azure Firewall Uses**
- Standalone resource
- Stateful firewall as a service
- Built-in high availability with unrestricted cloud scalability
- Create, enforce and log application and network connectivity policies
- Threat intelligence-based filtering
- Fully integrated with Azure Monitor for logging and analytics
- Support for hybrid connectivity through deployment behind VPN and ExpressRoute Gateways

FQDNs - Fully Qualified Domain Names

## Azure DNS

**Identity Domains and Custom Domains**
- When you create a new AAD Tenant, a new default domain is created
- The domain has initial domain name in the form of domainname.onmicrosoft.com
- You can customise/change the name
- After the custom name is added it must be verified - this demonstrates ownership of the domain.

**DNS Resolutions**
User: mail.microsoft.com > DNS Server (business.com): I don't look after that, forward request to ISP > ISP: I don't know that, forward to root server for hint (https://www.iana.org/domains/root/servers) > Root Server: Try this server for .com address > ISP: .com server what is this? > .com server: dunno try asking micrsoft.com address > ISP: Microsoft what is this? > Oh its this: zzz.zzz.zzz.zzz

DNS Zone notes here (Screnshots in the 20s)

**Private DNS Zones**
- Use your own custom domain names
- Provides name resolution for VMs within a VNet and between VNets
- Automatic hostname record management
- Removes the need for custom DNS solutions
- Use all common DNS record types
- Available in all Azure regions

**Types ofDNS records**
- A Record (Address Record): Maps a domain name to an IPv4 address.
- AAAA Record (IPv6 Address Record): Maps a domain name to an IPv6 address.
- CNAME Record (Canonical Name Record): Redirects one domain name to another. Often used for subdomains.
- MX Record (Mail Exchange Record): Specifies the mail servers responsible for receiving email for a domain.
- TXT Record (Text Record): Holds text information for various purposes, such as verification and security.
- NS Record (Name Server Record): Indicates the authoritative name servers for a domain.
- PTR Record (Pointer Record): Provides a reverse lookup, mapping an IP address to a domain name.
- SRV Record (Service Record): Defines the location of specific services, like servers or other network services.
- SOA Record (Start of Authority Record): Contains administrative information about the domain, including the primary name server and the email of the domain administrator.

**Azure Firewall**

- Source Network Address Translation (SNAT)
  - Purpose: SNAT is used for outbound traffic. It translates the private IP address of a source device to a public IP address before sending the traffic to the internet.
  - Why Use It?: This helps to hide the internal IP addresses of your devices, providing an extra layer of security. It also allows multiple devices to share a single public IP address for outbound traffic.
- Destination Network Address Translation (DNAT)
  - Purpose: DNAT is used for inbound traffic. It translates the public IP address of incoming traffic to a private IP address of a device within your network.
  - Why Use It?: This allows external users to access services hosted on private IP addresses within your network. It's commonly used for hosting web servers, mail servers, or other services that need to be accessible from the internet.

**Connecting VNets together**

VNet peering
- Two types of peering
  - Global
  - Regional
- Connects two Azure virtual networks - you can peer across subscriptions and tenants
- Peered networks use the Azure backbone for privacy and isolation
- Easy to setup, seamless data transfer and great performance
- **You can not have ip address crossover**

VPN Gateways
- Image 32 or 33

VPN Gateway SKUs
table Image 34

High Availability Scenarios
- Active/standby
- Active/active

In peering we pay 1 cents per GB or more for global and other options in that range both inbound and outbound traffic

VPN Gateway you pay per hour on data transfers you pay only for data coming out of Azure, Inbound traffic is free.


**ExpressRoute**
- Private connections between your on-premises network and Microsoft datacentre
- Connections do not go over the public Internet - Partner network
- Secure
- Reliable
- Low latency

Picture 38 for more details

Coexist Site-to-Site
Picture 39

**Virtual WAN**
- Brings together S2S (Site-to-Site), P2S (Point-to-site) and ExpressRoute
- Integrated connectivity using the hub-spoke connectivity model
- Connect virtual networks and workloads to the Azure hub automatically
- Visualise the end-to-end flow within Azure
- Two types:
  - Basic
  - Standard

**System Routes**
- Traffic between VMs in the same subnet
- Between Vms in different subnets in the
- See image 43

**User defined routes**
see image 44
Done using a Route table resource

**Service endpoints**
Endpoints limit network access to specific services

**Private endpoint**
image 50

## Administer network traffic
- Application Gateway (In Scope): Optimise delivery from application server farms while increasing application security with web application firewall
- Front Door: Scalable security-enhanced delivery point for global, microservice based web applications.
- Load Balancer (In Scope): Balance inbound and outbound connections and requests to your application or server endpoints
- Traffic Manager: Distribute traffic to services across global Azure regions, while providing hig availability and responsiveness

**Load Balancer**
- Distribute inbound traffic to the backend resources using load-balancing roads and health probes
- Can be used for both inbound/outbound scenarios
- Trow types:
  - Public
  - Internal


**Public Load Balancer**
- Maps public IP addresses and port number of incoming traffic to the VMs private IP address and port number and vice versa
- Apply load balancing rules to distribute traffic acros VMs or services

**Internal Load Balancer**
- Image 62

**Load Balancer SKUs**
- Basic
- Standard
Image 63 for table

**Backend Pools**
Image 64

**Load balancer rules**
- Maps frontend IP and port combination to a set of backend pool and port combinations
- Rules can be combined with NAT rules
- A NAT rule is explicitly attached to a VM (or network interface) ti complete the path to the target

**Session Persistence**
- Session persistence specifies how client traffic is handled
  - None (default): requests can be handled by any virtual machine
  - Client IP: requests will be handled by the same virtual machine
  - Client IP and Protocol: Specifies tht successive requests from the same address and protocol will be handled by the same virtual machine.

**Health Probe**
- Allows the load balancer to monitor the status of an app
- Dynamically adds or removes VMs from the load balancer rotation based on their response to health checks
- HTTP custom probe (preferred) pings every 15 seconds
- TCP custom prob tries to establish a successful TCP session

### Application Gateway
- Manages web app requests
- Routes... see image 67

**Application Gateway Routing**
Regional, for global use Front Door
- Path based routing
- Multiple-site routing

**Network Watcher**
Allows for a range of network diagnostic tools
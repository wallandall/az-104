# Virtual Networking

Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure. VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the internet, and on-premises networks. VNet is similar to a traditional network that you'd operate in your own data center, but brings with it additional benefits of Azure's infrastructure such as scale, availability, and isolation.

Virtual Networks concist of:

- Address Space: The Private address space for the isolated network. Required to provide resources with private IPs.
- VNet: The isolated network on Azure cloud where Azure resources like VMs are deployed.
- Subnets: The segmentation of the isolated network into smaller sub-networks where resources will exisit

Useful Links :
- [Design an IP addressing schema for your Azure deployment](https://docs.microsoft.com/en-us/learn/modules/design-ip-addressing-for-azure/)
- [Design an IP addressing schema for your Azure deployment](https://docs.microsoft.com/en-us/learn/modules/configure-network-for-azure-virtual-machines/)
- [Azure Virtual Network concepts and best practices](https://docs.microsoft.com/en-us/azure/virtual-network/concepts-and-best-practices)

# Deploying Network Resources 

Types of IP Addresses:

- Private IP Addresses: Statically or Dynamicaly assign addresses that allow private connectivity between resources. More information on Private IP Addresses can be found [here](https://docs.microsoft.com/en-us/azure/virtual-network/ip-services/private-ip-addresses)
- Public IP Addresses: Statically or dynamically assign addresses that allow public connectivity from the internet to a resource. More information on Public IP Addresses can be found [here](https://docs.microsoft.com/en-us/azure/virtual-network/ip-services/public-ip-addresses)


IP CIDR Planning allows you to plan your network to prevent overlap in network address space and allow for network integration. Click [here](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) for more information on CIDR Planning 

Click [here](https://docs.microsoft.com/en-us/learn/modules/design-ip-addressing-for-azure/) for information on ho to Design an IP addressing schema for your Azure deployment

## Routing Virtual Networks

Routes are the paths for connectivity between resources in our network as well as the inbound and outbound connectivity

Types of Routes:

- System Routes: Default routes built in to virtual networks that cannot be modified.
- Custom Routes: User defined routes or border gateway protocol(BGP) routes that overide system routes.

## Network Security Groups

[Network Security Groups (NSG)](https://docs.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview) control the traffic flowing through a virtual network. This is done by :

- Creating rules that define what is allowed/denied.
- Controlling security at the subnet or NIC network layers.
- Specifying rule priority

## Using Azure DNS

Azure DNS is a hosting service for DNS domains that provides name resolution by using Microsoft Azure infrastructure.

DNS, or the Domain Name System, is a protocol within the TCP/IP standard. DNS serves an essential role of translating the human-readable domain names, for example: www.wideworldimports.com, into a known IP address. IP addresses enable computers and network devices to identify and route requests between themselves.

DNS uses a global directory hosted on servers around the world. Microsoft is part of that network that provides a DNS service through Azure DNS.

A DNS server is also known as a DNS name server, or just a name server.

### How does DNS work?

A DNS server carries out one of two primary functions:

- Maintains a local cache of recently accessed or used domain names and their IP addresses. This cache provides a faster response to a local domain lookup request. If the DNS server can't find the requested domain, it passes the request to another DNS server. This process repeats at each DNS server until either a match is made or the search times out.
- Maintains the key-value pair database of IP addresses and any host or subdomain over which the DNS server has authority. This function is often associated with mail, web, and other internet domain services.

### IPv4 and IPv6
Every computer, server, or network-enabled device on your network has an IP address. An IP address is unique within your domain. There are two standards of IP address: IPv4 and IPv6.

- IPv4 is composed of four sets of numbers, in the range 0 to 255, each separated by a dot. Example: 127.0.0.1. Today, IPv4 is the most commonly used standard. Yet, with the increase in IoT devices, the IPv4 standard will eventually be unable to keep up.
- IPv6 is a relatively new standard and will eventually replace IPv4. It's made up of eight groups of hexadecimal numbers, each separated by a colon. Example: fe80:11a1:ac15:e9gf:e884:edb0:ddee:fea3.

Many network devices are now provisioned with both an IPv4 and an IPv6 address. The DNS name server can resolve domain names to both IPv4 and IPv6 addresses.

### DNS record types
Configuration information for your DNS server is stored as a file within a zone on your DNS server. Each file is called a record. The following record types are the most commonly created and used:

- A is the host record, and is the most common type of DNS record. It maps the domain or host name to the IP address.
- CNAME is a Canonical Name record that's used to create an alias from one domain name to another domain name. If you had different domain names that all accessed the same website, you would use CNAME.
- MX is the mail exchange record. It maps mail requests to your mail server, whether hosted on-premises or in the cloud.
- TXT is the text record. It's used to associate text strings with a domain name. Azure and Microsoft 365 use TXT records to verify domain ownership.

Additionally, there are the following record types:

- Wildcards
- CAA (certificate authority)
- NS (name server)
- SOA (start of authority)
- SPF (sender policy framework)
- SRV (server locations)

The SOA and NS records are created automatically when you create a DNS zone by using Azure DNS.

### Why use Azure DNS to host your domain?

Azure DNS is built on the Azure Resource Manager service, which offers the following benefits:

- Improved security
- Ease of use
- Private DNS domains
- Alias record sets

## Using Azure Firewall

Azure Firewall is a cloud-native and intelligent network firewall security service that provides the best of breed threat protection for your cloud workloads running in Azure. It's a fully stateful, firewall as a service with built-in high availability and unrestricted cloud scalability. It provides both east-west and north-south traffic inspection.

Azure Firewall is offered in two SKUs: Standard and Premium.

Azure Firewall Standard provides L3-L7 filtering and threat intelligence feeds directly from Microsoft Cyber Security. Threat intelligence-based filtering can alert and deny traffic from/to known malicious IP addresses and domains which are updated in real time to protect against new and emerging attacks.

![image](img/firewall-standard.png)

### Azure Firewall Premium

Azure Firewall Premium provides advanced capabilities include signature-based IDPS to allow rapid detection of attacks by looking for specific patterns. These patterns can include byte sequences in network traffic, or known malicious instruction sequences used by malware. There are more than 58,000 signatures in over 50 categories which are updated in real time to protect against new and emerging exploits. The exploit categories include malware, phishing, coin mining, and Trojan attacks.

![image](img/firewall-premium.png)

### Azure Firewall Manager
You can use Azure Firewall Manager to centrally manage Azure Firewalls across multiple subscriptions. Firewall Manager leverages firewall policy to apply a common set of network/application rules and configuration to the firewalls in your tenant.

Firewall Manager supports firewalls in both VNet and Virtual WANs (Secure Virtual Hub) environments. Secure Virtual Hubs use the Virtual WAN route automation solution to simplify routing traffic to the firewall with a few clicks.

To learn more about Azure Firewall Manager, see [Azure Firewall Manager](https://docs.microsoft.com/en-us/azure/firewall-manager/overview)

## Using Service Endpoints

[Virtual Network (VNet) service endpoint](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview) provides secure and direct connectivity to Azure services over an optimized route over the Azure backbone network. Endpoints allow you to secure your critical Azure service resources to only your virtual networks. Service Endpoints enables private IP addresses in the VNet to reach the endpoint of an Azure service without needing a public IP address on the VNet.


## Using Private Endpoint

[A private endpoint](https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-overview) is a network interface that uses a private IP address from your virtual network. This network interface connects you privately and securely to a service that's powered by Azure Private Link. By enabling a private endpoint, you're bringing the service into your virtual network.

[Back](ReadMe.md)

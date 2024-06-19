# VPC Components

This module  explore techniques network security controls in AWS and learn VPC security mechanisms such as Security Groups, Network Access Control List & Bastion hosts.

## Learning Objectives
- Describe the concepts of networking and its security aspects in AWS.
- Analyze Security Groups and Network Access Control lists in AWS.
- Explore the uses of Bastion Hosts in AWS.

## Virtual Private Cloud (VPC)
A VPC is composed of Regions, Availability Zone (AZ), Internet Gateways, Routers (Route Table), subnets and resources within the subnets.
- Regions: Physical locations where servers and data centers are
- Availability Zones (AZ): different data centers within a region. These AZs are within 60-mile radius of each other, which ensure the availabilities of services while reducing their latency.
- Internet Gateway: a component that connects resources within the VPC to the Internet.
    - Egress-only Gateway: allows IPv^ address to initiate outbound connections to the internet. No inbound connection is allowed.
- NAT gateways: allow resources in private subnets to communicate with those outside fo VPCs.
- Router: provides routing to the resources within the VPC so they can communicate with the Internet via the Internet Gateway.
- Subnets: Segmented networks of the VPC, which can be used for different purposes.

## VPC Security
### Security Groups
- By default, all traffics are denied
- acts as a virtual firewall that manages traffic coming in & going out of the VPC.
- Is stateful: if an inbound traffic is allowed, the response (outbound traffic) will be automatically allowed.

### Network Access Control Lists
- By default, allows all traffic
- Only applies to subnets
- Is stateless: an outbound rule still needs to be allowed even if inbound traffic is granted.

## Bastions Hosts
Provide a secure way for external entities to communicate with private resoures. 
Consider the following diagram

![Untitled Diagram drawio](https://github.com/hhphu/Cloud/assets/45286750/5ff20bfd-88fa-44a8-b083-1b990ad16ecb)

- If we want to access EC1 from the Internet, we should not provide a direct communication channel because it will pose security risks.
- In this case, we use Bastion Host as a jumnp server that allows communications between EC1 and the Internet. We can configure Security Group rules to secure the communication between the Internet and resources in private subnets.

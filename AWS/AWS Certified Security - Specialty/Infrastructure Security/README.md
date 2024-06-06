# AWS Infrastructure Security

AWS: Infrastructure Security Course is the second course of Exam Prep SCS-C02: AWS Certified Security – Specialty Specialization. This course assists learners to design security controls for edge services such as AWS WAF and AWS Shield. This course is basically divided into two modules and each module is further segmented by Lessons and Video Lectures. This course facilitates learners with approximately 3:00-3:30 Hours of Video lectures that provide both Theory and Hands-On knowledge. Also, Graded and Ungraded Quizzes are provided with every module in order to test the ability of learners. 

- Module 1: Network Security Controls: VPC Components
- Module 2: Network Security Controls: VPC Peering and Endpoints
- Module 3: Security Controls for Edge Services in AWS


## Network Security Controls: VPC Components

This module  explore techniques network security controls in AWS and learn VPC security mechanisms such as Security Groups, Network Access Control List & Bastion hosts.

**Learning Objectives**
- Describe the concepts of networking and its security aspects in AWS.
- Analyze Security Groups and Network Access Control lists in AWS.
- Explore the uses of Bastion Hosts in AWS.


### VPC Components
A VPC is composed of Regions, Availability Zone (AZ), Internet Gateways, Routers (Route Table), subnets and resources within the subnets.

**Security Groups**: 
- By default, all traffics are denied
- acts as a virtual firewall that manages traffic coming in & going out of the VPC.
- Is stateful: if an inbound traffic is allowed, the response (outbound traffic) will be automatically allowed.

**Network Access Control Lists**
- By default, allows all traffic
- Only applies to subnets
- Is stateless: an outbound rule still needs to be allowed even if inbound traffic is granted.
- We can assign rules numbers to determine the importances of the rule. The smaller the number, the higher the order.


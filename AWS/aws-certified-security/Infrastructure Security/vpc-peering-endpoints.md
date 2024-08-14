# VPC Peering and Endpoints

## NAT Gateway
**1. Purpose of NAT Gateway:**
   - The NAT gateway allows an Amazon EC2 instance in a private subnet to initiate requests to the internet.
   - It takes the request from the instance, sends it to the internet, receives the response, and forwards it back to the instance.

**2. Differences between NAT Gateway and NAT Instance:**
   - NAT gateway is an AWS managed service, while NAT instance requires manual management.
   - NAT gateway supports up to 5 gigabytes of bandwidth and can automatically scale up to 45 gigabytes per second.
   - NAT gateway does not require managing the underlying EC2 instance, unlike NAT instance.

**3. Implementing NAT Gateway:**
   - NAT gateway is a separate service available in AWS.
   - It is highly available and can be implemented across multiple availability zones.
   - It automatically gets assigned a private IP address from the subnet's address pool.

**4. Security Groups and NAT Gateway:**
   - You cannot associate a security group directly with a NAT gateway.
   - Instead, you work with security groups assigned to the instances in the private subnet.

**5. NAT Gateway and Bastion Host:**
   - Unlike a NAT instance, you cannot double a NAT gateway as a bastion host.


## VPC Peering
**1. What is VPC peering?**
- VPC peering is a network connection between two VPCs that allows traffic to be routed across the connection.
- VPC peering can be established between VPCs in different AWS accounts and different regions.

**2. How to implement a VPC peering connection?**
- One VPC must send a request to another VPC for creating a VPC peering connection.
- The receiving VPC must accept the peering connection request.
- Routes must be added in the route table of both VPCs to ensure traffic can be routed between them.
- Security groups attached to the instances' elastic network interfaces must allow inbound traffic.

**3. Characteristics of a VPC peering connection:**
- Multiple VPC peering connections can be created for a VPC.
- VPC peering does not support transitive relationships, so direct peering connections are required between VPCs for communication.
- VPCs for peering must not have overlapping CIDR blocks.
- VPCs with certain connections like VPN, AWS Direct Connect, or Internet connections via gateways or NAT devices cannot extend the peering relationship.

VPC peering allows communication between Amazon EC2 instances in different VPCs, enabling better connectivity and flexibility in your AWS infrastructure.

## VPC Endpoints
- Acts as a virtual device that allows private subnet to route requests to S3 without going through the Internet.
- There are two types of VPC endpoints:
   - Gateway endpoints: for connecting to S3 and DynamoDB
   - Interface endpoints: connecting to other AWS services.

### VPC Endpoints Policies
- Determine who can access AWS services through these endpoints -> ensure only authroized users/resources can connect to the services.
In this chapter, we explore the concept of policies for VPC endpoints and S3 buckets in AWS. Policies are sets of rules that control access to AWS services and resources.

For VPC endpoints, we can create policies to determine who can access AWS services through those endpoints. This helps ensure that only authorized users or resources can connect to the services.

### AWS Inspector
- Used to test network accessibility and security of Amazon EC2 Instances.
- Scan applications for vulnerabilities and deviations from best practices.
- Need to install an agent on EC2 instance for host assessments while network assessments do not need an agent.



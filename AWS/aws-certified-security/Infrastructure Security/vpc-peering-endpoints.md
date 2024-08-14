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


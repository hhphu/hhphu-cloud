# AWS Edge Services

## AWS Load Balancer
#### 1. **Introduction**
   - **Objective:** Learn how to secure connections to AWS Elastic Load Balancer (ELB) and implement SSL.
   - **Key Topics:**
     - Securing connections to AWS ELB.
     - Implementing SSL for AWS ELB.

#### 2. **Securing Connections to AWS Elastic Load Balancer**
   - **Secure Connections:** 
     - AWS allows the definition of a load balancer to accept secure connections.
     - **SSL/TLS Encryption:** All connections between the client and the ELB are encrypted using SSL or TLS protocols.
     - **SSL Offloading:** The encryption process (SSL/TLS) is terminated at the ELB, reducing the load on backend servers.
   - **Backend Connections:**
     - Can be configured to be secure (encrypted) or insecure (unencrypted) depending on the application requirements.

#### 3. **Steps to Secure Traffic to AWS ELB**
   - **Add HTTPS Listener:**
     - Ensures that the load balancer can accept HTTPS traffic.
   - **Security Groups Configuration:**
     - Ensure that the security groups associated with the load balancer allow traffic on HTTPS (port 443).
   - **Deploy SSL Certificate:**
     - An SSL certificate must be installed on the load balancer to enable SSL/TLS encryption.
   - **Use Security Policies:**
     - Security policies are used to negotiate secure connections between clients and the load balancer.

#### 4. **SSL Offloading and Backend Security**
   - **Application Load Balancer (ALB):**
     - When users connect securely via SSL, the SSL connection is terminated at the ALB.
     - **Backend Instances:**
       - If you want backend connections to also be secure, SSL can be implemented on backend EC2 instances as well.
       - **Port Configuration:**
         - Backend instances can listen on port 80 (insecure) or port 443 (secure).

## AWS CloudFront
#### 1. **Introduction**
   - **Objective:** Understand how to enhance security with AWS CloudFront.
   - **Key Topics:**
     - Using HTTPS with CloudFront.
     - Restricting access to files in Amazon S3 buckets through CloudFront.

#### 2. **Using HTTPS with CloudFront**
   - **Configuring HTTPS:** 
     - **Purpose:** Ensure that users access objects via CloudFront securely using HTTPS.
     - **SSL/TLS Negotiation:** 
       - When a user submits an HTTPS request, SSL/TLS negotiation occurs between the user and CloudFront.
       - If the requested object is cached in CloudFront, it is encrypted and returned to the user.
       - If the object is not cached, CloudFront negotiates SSL/TLS with the origin server, retrieves the encrypted object, decrypts it, re-encrypts it, and then sends it back to the user.

#### 3. **Restricting Access to Amazon S3 Buckets**
   - **Default Behavior:**
     - By default, S3 buckets need to be publicly accessible for users to fetch objects via CloudFront, which can expose the bucket to direct access.
   - **Origin Access Identity (OAI):**
     - **Solution:** Use CloudFront's Origin Access Identity to restrict direct access to S3 buckets.
     - **Implementation:**
       - CloudFront creates a special identity (OAI) that is granted read access to the S3 bucket.
       - This ensures that objects in the S3 bucket are only accessible through CloudFront and not directly via the S3 URL.

## AWS Web Application Firewall
### Key Points:
1. **Introduction to AWS WAF**:
   - AWS WAF is used to monitor and control HTTP and HTTPS requests to AWS resources like API Gateway, CloudFront, and Application Load Balancer.
   - It helps protect against attacks such as cross-site scripting, SQL injection, and requests from specific locations.

2. **Setting Up WAF**:
   - **Web Access Control List (Web ACL)**: A Web ACL is created to define protection rules.
   - **Rules**: Within the Web ACL, rules are defined, and conditions are set based on attack types or IP addresses.
   - **Conditions**: Conditions like IP address filtering, cross-site scripting protection, or SQL injection protection are defined first.

## AWS Shield
#### Key Concepts:
1. **DDoS Attacks**: 
   - A DDoS attack involves flooding a web application with excessive network traffic, rendering the application inaccessible. This can disrupt normal user access and cause significant downtime.

2. **AWS Shield Tiers**:
   - **AWS Shield Standard**:
     - Automatically included at no extra cost.
     - Protects against network and transport layer DDoS attacks.
   - **AWS Shield Advanced**:
     - A premium service costing around $3,000 per month.
     - Provides enhanced protection, including application-level monitoring, real-time metrics, and 24/7 support from the DDoS Response Team.
     - Suitable for high-profile applications utilizing Amazon EC2, Elastic Load Balancer, Amazon CloudFront, or Amazon Route 53.

#### Practical Application:
- AWS Shield can be accessed through the AWS Management Console under the "WAF and Shield" section.
- The service offers comprehensive protection features, with AWS Shield Advanced providing additional support and insights during large-scale DDoS attacks.

## EC2 Instance Detection and Prevention
#### Key Concepts:
1. **Intrusion Detection and Prevention**:
   - **Purpose**: IDPS are used to monitor networks and systems for malicious activities.
   - **Functionality**: These systems detect, prevent, and alert administrators of potential incidents, blocking or dropping malicious traffic when necessary.

2. **Implementation on AWS**:
   - **Third-Party Tools**: IDPS tools are available through the AWS Marketplace. You can subscribe to these tools and integrate them into your AWS environment.
   - **Integration**: Upon subscribing to a service like Alert Logic, the tool integrates with your AWS account by deploying an IAM role that monitors and performs threat detection across your AWS resources.

3. **Vendor Selection and Configuration**:
   - **AWS Marketplace**: Various vendors offer IDPS tools with different pricing and features.
   - **Setup**: After subscribing, you'll likely need to create an account with the vendor and configure the service to monitor your AWS environment. The system can provide security recommendations and monitor specific regions, VPCs, and subnets in your account.

This chapter provided an overview of how to implement and utilize Intrusion Detection and Prevention Systems within your AWS infrastructure, emphasizing the importance of these tools in maintaining a secure environment.

## AWS Lambda Security
Here’s a summarized version of the chapter on AWS Lambda security:

---

### AWS Lambda Security Overview
#### Key Concepts:
1. **Permissions and Access Control**:
   - **IAM Permissions**: Ensure that the correct IAM permissions are set for users who need access to the AWS Lambda service.
   - **IAM Roles**: Use IAM roles to control access from AWS Lambda to other AWS services. For example, if your Lambda function needs access to an S3 bucket, create and attach an IAM role with the necessary permissions to the Lambda function.

2. **Monitoring and Logging**:
   - **CloudTrail**: Enable AWS CloudTrail to monitor API activity and user actions within your AWS environment, including activities related to Lambda.

3. **Security Measures for Lambda**:
   - **Secure Connections**: By default, all Lambda API endpoints support secure connections only.
   - **Environment Variables**: Store secrets, such as database passwords, securely in environment variables. Use AWS Key Management Service (KMS) to encrypt these environment variables to ensure their security.

4. **Practical Implementation**:
   - **Adding Execution Roles**: Within the AWS Lambda console, you can add an execution role to a Lambda function to grant it permissions to interact with other AWS services.
   - **Encrypting Environment Variables**: When adding environment variables (e.g., `dbpassword`), utilize AWS KMS to encrypt them, ensuring that sensitive data is protected.

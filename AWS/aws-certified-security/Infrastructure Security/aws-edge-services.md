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

#### 5. **Lab Overview**
   - **Lab Activities:**
     - Create an EC2 instance using a WordPress AMI.
     - Create an Application Load Balancer.
     - Test the load balancer.
     - Use Route 53 to add an alias record for the load balancer.
     - Add an HTTPS listener for the load balancer.
   - **Objective:** Implement the security measures discussed, including SSL/TLS and HTTPS configuration.

This study note summarizes the key points from the lesson on securing connections with AWS Elastic Load Balancer and the steps needed to implement SSL for secure communication.
## AWS CloudFront
- HTTPS with CloudFront:
  - You can configure HTTPS with CloudFront to ensure secure communication between users and CloudFront.
  - When a user submits an HTTPS request to CloudFront, an SSL/TLS negotiation occurs between the user and CloudFront.
  - If the requested object is in the cache, CloudFront encrypts the response and sends it back to the user.
  - If the object is not in the cache, CloudFront performs an SSL/TLS negotiation with the origin (e.g., an S3 bucket), retrieves the encrypted object, decrypts it, re-encrypts it, and then sends it back to the user.

- Restricting Access to Files in Amazon S3 Buckets:
  - By default, users need public access to an S3 bucket to access objects via CloudFront.
  - To add an extra layer of security, you can allow CloudFront to create an origin access identity.
  - The origin access identity is a special identity that CloudFront creates and gives access to read files from the underlying S3 bucket.
  - This ensures that users can only access the objects through CloudFront and not directly from the S3 bucket.

## AWS Web Application Firewall
- AWS Web Application Firewall Service:
  - Monitors and controls HTTP and HTTPS requests to AWS resources.
  - Protects web infrastructure against attacks like cross-site scripting and SQL code injection.
  - Can block requests from specific locations or countries.
  - Uses web access control lists, rules, and conditions to define protection criteria.
- Creating a Web Access Control List:
  - Define conditions based on different types of attacks (e.g., cross-site scripting, IP addresses).
  - Create rules that specify which conditions to apply.
  - Associate the web access control list with AWS resources like an application load balancer.
- Benefits of the Web Application Firewall Service:
  - Protects web infrastructure against various types of attacks.
  - Provides flexibility in defining rules and conditions.
  - Offers marketplace options for easier rule creation.
  - Allows for easy removal and cleanup of resources.

## AWS Shield
- AWS Shield is a service provided by Amazon Web Services (AWS) that helps protect against distributed denial of service (DDoS) attacks.
- DDoS attacks involve flooding a web application with a large amount of network traffic, making it inaccessible to users.
- AWS Shield offers two pricing tiers: AWS Shield Standard and AWS Shield Advanced.
  - **AWS Shield Standard** is automatically available for all AWS accounts at no additional charge. It protects against network and transport layer DDoS attacks.
  - **AWS Shield Advanced** provides a higher level of protection for applications using services like Amazon EC2, Elastic Load Balancer, Amazon CloudFront, and Amazon Route 53.
    - With AWS Shield Advanced, you can also access a 24/7 DDoS response team for assistance during an actual DDoS attack.
    - AWS Shield Advanced offers advanced real-time metrics and reports to provide insights on DDoS attacks.
- To find AWS Shield in the AWS console, you can search for "WAF and Shield" (Web Application Firewall and Shield).

## EC2 Instance Detection and Prevention chin chu- Intrusion detection and prevention systems are used to monitor networks and systems for malicious activity.
- These systems add an extra layer of security to infrastructure.
- They can detect and prevent malicious activity, alert administrators of possible incidents, and block attacks or intrusions.
- Third-party tools from the AWS marketplace are needed to implement intrusion detection and prevention systems.
- The AWS marketplace offers various vendors and products for this purpose.
- Users can subscribe to a product, integrate it with their AWS account, and deploy an IAM role for threat detection.
- These systems also provide recommendations for improving security in the AWS account.

## AWS Lambda Security
In this chapter on the security of the AWS Lambda service, we learn about various security aspects and features that can be used to ensure the safety of your Lambda functions. Here are the key points covered:
1. Set the right permissions: It is important to ensure that the appropriate permissions are set for users to access the AWS Lambda service.
2. Enable CloudTrail: By enabling CloudTrail, you can monitor API activity and user activity, providing you with visibility and control over your Lambda functions.
3. Use IAM roles: IAM roles can be used to control access to other AWS services. If your Lambda function needs to access objects in an S3 bucket, you can create an IAM role and attach it to the Lambda function to grant the necessary permissions.
4. Secure connections: By default, all Lambda API endpoints only support secure connections, ensuring that data is transmitted securely.
5. Use environment variables: Environment variables can be used to store secrets securely that need to be used within AWS Lambda. For example, you can store a database password as an environment variable and reference it in your Lambda function.
6. Encrypt environment variables with AWS KMS: To further enhance security, you can allow AWS Key Management Service (KMS) to encrypt the environment variables, ensuring that sensitive information is protected.

Remember to review the AWS Lambda service and explore the options available to set permissions, manage IAM roles, and configure environment variables securely.

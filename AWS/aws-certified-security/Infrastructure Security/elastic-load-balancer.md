# AWS Edge Services

## AWS Load Balancer
- Securing connections to the AWS Elastic Load Balancer:
  - Define a load balancer in AWS to accept secure connections.
  - All connections between the client and the load balancer are encrypted using SSL or TLS protocols.
  - This is known as SSL offloading.
- Steps to ensure secure traffic:
  - Add an HTTPS listener to the load balancer.
  - Allow traffic on HTTPS in the load balancer's security groups.
  - Deploy an SSL certificate onto the load balancer.
  - Use a security policy for the load balancer to negotiate connections between clients and the load balancer.
- Implementing SSL on backend EC2 instances:
  - SSL connection is terminated at the application load balancer (SSL offloading).
  - Backend connections between the load balancer and EC2 instances can also be secured by implementing SSL on the instances.
  - Backend instances can listen on port 80 or port 443, depending on the desired level of security.

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

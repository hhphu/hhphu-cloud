# AWS Security: Threat Detection, Logging and Monitoring

![Header Image](https://images.spiceworks.com/wp-content/uploads/2021/06/04113234/shutterstock_1530570248-1.jpg)

This domain is designed to detect security threats and identify their root cause using security best practices.  This also focuses on Shared Responsibility Model and security best practices dealing with IAM users and EC2 Instances. There are 2 modules in this domain:
- Threat Detection and Incident Response in AWS
- Logging and Monitoring in AWS

-----
# Incident Response Planning
An Incident Response Plan is crucial for manaing and mitigating security incidents, ensuring quick and efficient recovery, and maintaining trust with stakeholders. 
## Core principles of Incident Respons
### 1. Educate
Educate your stakeholders — this includes both your customers and your IT support staff. Everyone involved should be well-versed in the Incident Response Plan.
- Customers need to understand how to react if they notice suspicious activities.
- IT support staff must know their roles and responsibilities during an incident.
### 2. Prepare
Preparation is critical. Ensure your IT support staff is ready to handle incidents:
- Incident Response Plan: Develop and disseminate a clear and actionable plan.
- Training: Regularly train staff on response protocols and mitigation strategies.
### 3. Simulate
Test the effectiveness of your response plan through simulation:
- Conduct regular simulations to identify strengths and weaknesses.
- Ensure that the response plan is practical and effective under various scenarios.
### 4. Iterate
Constantly review and improve your response plan:
- Regular reviews: Adjust the plan to reflect changes in your environment and AWS updates.
- Feedback loop: Incorporate lessons learned from simulations and real incidents.

## Designing Your Incident Response Plan
When designing your response plan, consider the following critical aspects:
### Response Objectives
Define clear objectives for your response plan:
- Stakeholder Expectations: Understand what your users and customers expect during an incident.
- Mitigation Plans: Develop strategies to minimize damage and restore normal operations.
- Data Preservation: Ensure critical data is preserved for forensic analysis.

### Data Management
Identify the types of data you need and how to collect them:
- Data Collection: Utilize tools like AWS CloudWatch and AWS CloudTrail to gather logs and other relevant data.
- Automation: Implement automated responses where possible to expedite incident handling.
- Scalability: Ensure your solutions can scale to handle incidents across different parts of your environment.

### AWS Tools and Services
Leverage AWS tools to enhance your incident response capabilities:
- AWS CloudWatch: For logging and monitoring.
- AWS CloudTrail: For tracking API calls.
- VPC Flow Logs: For monitoring traffic within your VPC.
You can also integrate third-party tools for threat intelligence and host intrusion detection.

### Response Plan Execution
Develop a detailed plan for executing your response:
- Dedicated Accounts: Use separate AWS accounts for investigating incidents to avoid contamination.
- IAM Policies: Ensure response teams have read-only access to necessary data and resources.
- Resource Isolation: Isolate affected resources to prevent further spread of the incident.

### Forensic Workstations
Creating forensic workstations is crucial for detailed investigation:
- Create an EC2 Instance: Start with a base Amazon Machine Image (AMI).
- Harden the Instance: Secure the underlying operating system.
- Install Forensic Tools: Use preferred third-party tools for analysis.
- Create and Maintain AMIs: Regularly update the AMI with the latest security patches.


- [AWS Security Incident Response Planning](https://medium.com/@harry.hphu/aws-security-incident-response-planning-191d7c9277b7)
- [Dealing with compromised IAM users](https://medium.com/@harry.hphu/aws-security-how-to-deal-with-compromised-iam-users-bc50614b387f)
- [Lab — Dealing with compromised AWS IAM Users](https://medium.com/@harry.hphu/lab-dealing-with-compromised-aws-iam-users-269dc5b889e7)
- [Securing EC2 instances in AWS](https://medium.com/@harry.hphu/securing-ec2-instances-in-aws-7c9da5f5b955)
- [Lab — EC2 instances with key pair](https://medium.com/@harry.hphu/lab-ec2-encryption-with-key-pair-9a918fed36e7)
- [Lab — EC2 instances monitoring](https://medium.com/@harry.hphu/lab-ec2-instances-monitoring-91d4ce6a9080)
- [AWS GuardDuty](https://medium.com/@harry.hphu/aws-security-amazon-guardduty-7cf5d0a44e89)

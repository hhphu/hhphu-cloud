# AWS Security: Threat Detection, Logging and Monitoring
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

-----
# Securing EC2 instances
## System status checks
System status checks are designed to ensure the underlying hardware and networking infreastructure of EC2 instances are functioning properly. The checks might fail due to:
- Loss of Network Connectivity: If the instance can’t communicate with other network resources.
- Loss of System Power: When the physical server hosting your instance loses power.
- Software Issues on the Physical Host: Problems with the software running on the physical server.
- Hardware Issues: Failures in the physical components that impact network reachability.

## Instance status checks
Instance status chechs focus on the configuration and operation of the individual instance itself. The checks may fail due to:
- Failed system status check: if the underlying system status check has already failed
- Exhausted memory: the instance runs out of memory
- Corrupted file systems: issues with the instances' file systems integrity
- Incompatible kernel: the instance's OS kernel is not compatible with the instance configuration
- Misconfigured Networking/Startup configuration: errors in network settings or the startup process.
These status checks are performed every minute and return either a pass or fail status. If one or more checks fails, the overall status is reported as "impaired".

## Creating alarms and Automated responses
AWS allows you to set up alarms based on the status checks. You can configure these alarms to notify you when an issue occurs and even automate responses to hanle the problem. For example:
-  Recover the instance: attempt to restore the instance to a healthy state.
-  Stop the instance: safely shut down the instance.
-  Terminate the instance: permanently remove the instance.
-  Reboot the instance: restart the instance to clear transient issues.
These automated actions help ensure minimal downtime and quicker resolutions of issues.

## CloudWatch metrics
In addition to status checks, AWS provides CloudWatch metircs for detailed monitoring of EC2 instances. These metrics include:
- CPU utilization: tracks the % of CPU capacity being used.
- Disk Read/Write: measures the # of read and write operations to the instance's disk.
- Network traffic: monitors the amount of data being sent & received by the instance.
These metrics are essential for understanding the performance and health of the instances. You can view these metrics on the CloudWatch dashboard and set up alarms  to notify you of unusual activiy.

## Dealing with compromised IAM users
When an IAM user is compromised, follow these steps:
1. Deactivate Access Keys: We should deactivate the user's access key immediately. **DO NOT DELETE** as the action may disrupt running applications that are associated with the acccess key.
2. Review assigned policies: Assess all policies assigned to the IAM user. 
  - View permission policies attached to the user to understand his/her access rights.
  - Check security credentials, including login methods (password, access keys)
  - Assess access key usage frequency to identify potential misuse.
  - Remove any policies associated with the user & and revoke his/her access permissions.
3. Check CloudTrail Events: Review CloudTrail events to identify any suspicious activities associated with the IAM user.
4. Manage user accounts:
- If the impact is minimal, deleate and create a new one.
- For users with long-term access credentials, considuer using IAM roles for safer short-term credentials.
 
-----
# Resources
- [Lab — Dealing with compromised AWS IAM Users](https://medium.com/@harry.hphu/lab-dealing-with-compromised-aws-iam-users-269dc5b889e7)
- [Lab — EC2 instances with key pair](https://medium.com/@harry.hphu/lab-ec2-encryption-with-key-pair-9a918fed36e7)
- [Lab — EC2 instances monitoring](https://medium.com/@harry.hphu/lab-ec2-instances-monitoring-91d4ce6a9080)


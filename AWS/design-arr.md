# Design for Availability, Reliability and Resiliency

![screenshot-2023-12-15-at-4 32 26pm](https://github.com/user-attachments/assets/4258e84d-8e8a-485b-a13d-d857dc430af2)

## Create VPCs
Create two VPCs, `primary-vpc` (us-east-1) and `secondary-vpc` (us-west-2):
1. Services -> CloudFormation
2. Create stack "With new resources (standard)"
   
   ![2024-02-02-11_02_13-stacks-_-cloudformation-_-us-east-1](https://github.com/user-attachments/assets/2ad56ba7-8e12-47ee-b08d-8b90997f62da)

3. Upload a template file
4. Click "Choose file" butotn
5. Select the 'vpc.yml` file
6. Next
7. Fill in the Stack name, `design-for-arr-primary` & `design-for-arr-secondary`
8. Name the VPCs: `primary-vpc` and `secondary-vpc`
9. Update the CIDR blocks to match the architecture diagram
10. Leave the next options as default and click Submit
11. Wait until the stacks are created

Confirm the stacks are created:

- **design-for-arr-primary**

![image](https://github.com/user-attachments/assets/8cf43fcf-5f0b-475e-853f-91eb98645d82)

- **design-for-arr-secondary**

![image](https://github.com/user-attachments/assets/438e8723-1da2-428e-80b5-8b65ed3d0beb)

- **primary-vpc**

![primary_vpc](https://github.com/user-attachments/assets/2f19f795-cf43-4487-9682-adc7c378a3f1)

- **Primary VPC subnets**

![image](https://github.com/user-attachments/assets/b7f9a750-62e6-4bfc-b103-0ea6571730d5)

- **secondary-vpc**

![image](https://github.com/user-attachments/assets/d6ae0fe0-a748-4ac1-8517-8838bff7938c)

- **Secondary VPC subnets**

![image](https://github.com/user-attachments/assets/542e95df-a4b5-4bbc-9775-9f351481811f)


## Data Durability And Recovery
### Highly durable RDS Database
In the primary region (us-east-1), create a new RDS Subnet group using the private subnets:
1. Create a new MySQL, multi-AZ database:

   ![image](https://github.com/user-attachments/assets/4bdb63d3-29e4-43e2-b183-fe7806f201ba)

  -  **Settings**
      - **DB instance identifier**: `arr-database`
      - **Master username**: `admin`
      - **Credentials Management**: `Self managed`
      - Enter the **Master password** and **Confirm master password**

  ![image](https://github.com/user-attachments/assets/69df495d-8a86-4a7c-8e96-b09b5a59a506)

  - **Instance configuration**
      - **Burstable classes (includes t classes)** > **db.t3.micro**

  ![image](https://github.com/user-attachments/assets/fdedf33f-c446-4c3d-9e2b-9baa1ff77bca)

  - **Connectivity**
    - **Virtual private cloud**: `primary-vpc`
    - **Public Access**: `No`
    - **VPC security group**: `Choose existing`
    - **Exiting VPC security groups**: `UDARR-Database`

  ![image](https://github.com/user-attachments/assets/882eeece-fb03-4d23-bc6c-4d51b78c1b59)

  - Expand the **Additional Configuration** section
    - **Initial database name**: `udacity`
    - **Enable automated backups**: `check`
    - **Log exports**: `Audit Log`, `Error Log`, `General Log`, `Slow query log`

  ![image](https://github.com/user-attachments/assets/2ddc7fd8-a5ee-487c-bb5f-bac583506653)


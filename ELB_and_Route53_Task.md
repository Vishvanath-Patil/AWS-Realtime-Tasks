
# Problem Statement
## You Work for XYZ Organization which uses On-Primise Solutions and limited number systems, With Increse in requests in their application, the load also increases to handle the load the corporate must buy more systems almost on regular basis, Realising need to cut down expenses on systems, so decided to move their infrastructure to AWS.

# Task To Be Performed 
## 1. Manage the Scaling Requirements by the Company by:
 a. Deploying Multiple Compute Resources on the Cloud as soon as the load increases and CPU Utilization exceeds 80%

 b. Removing the Resources When CPU Utilization goes under 60%  

## 2. Create Load Balancer to distribute the load between compute resources  
## 3. Route the Trrafic to Company's Domain 

### Create KeyPair
![Untitled 1](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/319da475-1cd6-40ca-86dc-5a836df7f1f2)

### Create Security Group and allow SSH and HTTP
![Untitled 2](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/af0e7fb4-e090-40b1-8eb2-2911aee3758b)

### Edit Inbound and Allow SSH and HTTP
![Untitled 3](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/2f925a52-d6b2-4d2c-8854-d0cffc9aa7a7)
Now Security Group Created Successfully.

## Create Target Groups
**Navigate to EC2 Dashborad —> LoadBalancing —> Target Groups —> Create Target Groups** 
![Untitled 4](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/10d6e5a0-5ea1-4f7d-9e25-3e365282abe9)

**Choose Target type Instances** 
![Untitled 5](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/3ce56d7e-531d-4107-9d57-10d75d1821b8)

**Then choose the name** 
![Untitled 6](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/1bcea506-4e7a-4516-82fa-3156d96c3697)
![Untitled 7](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/46df65e6-b203-453e-a62c-d1d65f991de6)

## Create Application Load Balancer

**Navigate to EC2 Dashboard —> Load balancing —> Load Balancer —> Create Load Balancer**
![Untitled 8](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/c6521d0a-592d-4482-a88a-466f3fee4e49)

**Select all Subnets** 
![Untitled 9](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/753fc0af-9ed1-4bf1-9d3e-ce50bc414431)

**Select Target Group** 
![Untitled 10](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/f9749b19-2ab3-406d-9eaa-472545e6bc41)
![Untitled 11](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/d0e102f3-147d-4378-81af-b573446c56a2)

**Load Balancer Created Successfully.**

## 3. Create Lanch Template

**Navigate to ⇒ EC2 Dashboard —> Instances —> Launch Templates**

- **Select OS as Amazon Linux**
- **Instance Type is t2.micro**
- **Select KeyPair**
- **Select the Security Group as WEBSG**

**In Advance Option Provide the user data script to make your website ready**

```jsx
#!bin/bash
yum update -u
yum install httpd -y
systemctl enable httpd
systemctl start httpd
echo "Welcome to my Website" > /var/www/html/index.html
systemctl restart httpd 

```
![Untitled 12](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/d7de536c-0a67-40ff-8593-1206d2eaeaae)

![Untitled 13](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/ff0072b0-573c-42e6-8a90-fcf965934ae6)
**Launch Template Created Successfully.**

## Create Auto-Scaling Groups
**Navigate ⇒ EC2 Dashboard —>Auto-Scaling Groups —> Create Auto Scaling Group**
![Untitled 14](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/4dbe4574-957f-49a5-acf0-2054c77d1852)

**Select all Subnets** 
![Untitled 15](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/2e007c3a-41ab-4cab-9713-e1ab5c84f027)

**Then choose exiting Load Balancer**
![Untitled 16](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/fa4f2871-dbf5-44d2-b95b-5dfa91885183)

**Turn On Elastic Load Balancing Health check** 
![Untitled 17](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/5e4c174b-b377-4730-bf13-8f92c4104048)
![Untitled 18](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/d77fddbe-0d72-49c0-8d45-12b47dd4b766)

**Simply Skip and next and complete the steps.**
![Untitled 19](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/ac9b76f0-0ebe-469f-80b3-a3e51312fc92)

**Now Successfully Created Auto-Scaling Group.**
![Untitled 20](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/2882371e-bafe-4821-a6ff-c20f59478217)

**Now ASG Working as expected.**
![Untitled 21](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/3bb829d8-a832-4b02-9d18-03303cc09d02)

## 4. Map the Company Domain.
![Untitled](https://github.com/Vishvanath-Patil/AWS-Realtime-Tasks/assets/130968991/97885e73-5dc7-45fc-a0e2-447183f40374)


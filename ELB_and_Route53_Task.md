
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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/5d8fcc3b-ae5d-4ac1-94ea-b7e4a6a63771/Untitled.png)

### Edit Inbound and Allow SSH and HTTP

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/b1ea89fd-39c4-45ad-a642-55f3cfe030b5/Untitled.png)

Now Security Group Created Successfully.

## Create Target Groups

**Navigate to EC2 Dashborad —> LoadBalancing —> Target Groups —> Create Target Groups** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/99763deb-6a05-4ed5-97d4-418ae9db15a8/Untitled.png)

**Choose Target type Instances** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/5c387036-f2bd-4c00-9714-4c669cf600e9/Untitled.png)

**Then choose the name** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/b9e0648f-cca4-468f-b694-24bd3fad69f6/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/b1b04ad9-e0fe-40e5-a480-e612fa5552f2/Untitled.png)

## Create Application Load Balancer

**Navigate to EC2 Dashboard —> Load balancing —> Load Balancer —> Create Load Balancer**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/c65afd4d-ac7d-41de-a154-a5524696fb52/Untitled.png)

**Select all Subnets** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/682ec571-d7ae-41dd-a50e-ac0fac088f1b/Untitled.png)

**Select Target Group** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/142afc5c-f2ab-4c18-9457-5e9167bdb6d3/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/4cfdaaff-a1c0-4fbd-ac6b-d2980f440fd6/Untitled.png)

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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/ab50acca-3e66-4d77-8ec2-ee846b594eeb/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/3943baba-1e38-4fe6-a380-9800f416b130/Untitled.png)

**Launch Template Created Successfully.**

## Create Auto-Scaling Groups

**Navigate ⇒ EC2 Dashboard —>Auto-Scaling Groups —> Create Auto Scaling Group**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/a9be2426-39a1-49da-aab8-d118108c05a0/Untitled.png)

**Select all Subnets** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/f2771419-1425-4de7-9872-4bcb7f446b89/Untitled.png)

**Then choose exiting Load Balancer**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/4990ba0d-8302-42c4-a930-9d0cb226e34f/Untitled.png)

**Turn On Elastic Load Balancing Health check** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/13c7b170-138b-49d8-a3d7-0c894fa29254/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/ae33ce0a-69bc-4e2e-85f0-73269dc821f0/Untitled.png)

**Simply Skip and next and complete the steps.**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/ca35b6e9-9b3b-4e52-a3da-f8040ae73a06/Untitled.png)

**Now Successfully Created Auto-Scaling Group.**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/7a562276-55a8-4eb1-bde3-cd6111f33b75/Untitled.png)

**Now ASG Working as expected.**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/57a705de-20fe-43c1-87e7-69e8a4de156f/Untitled.png)

## 4. Map the Company Domain.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cd45c56f-cde0-4b31-a477-4ec3fa5f480b/0d32f7c5-ca16-46fe-9479-9e41b5f727ac/Untitled.png)

## Introducing Today's Project!

In this project, I will demonstrate how to create a (Virtual Private Cloud) VPC.

I'm doing this project to learn how to create and configure an Amazon VPC in AWS, understand CIDR blocks and IP addressing, create public and private subnets, configure route tables and Internet Gateways, and build a secure, isolated network environment for hosting cloud resources.

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will create a VPC  because we are creating an Amazon Virtual Private Cloud (VPC) to establish a logically isolated network in AWS. We will define the IPv4 CIDR block, configure the network settings, and create a dedicated network where we can launch and manage AWS resources such as EC2 instances, subnets, and route tables securely.

### How VPCs work

To put it simply - without VPCs, every AWS resource would exist in one giant, open space in the cloud, like a country without cities or districts.

Resources would be randomly scattered with no privacy or personal space, so everyone could see and access everyone else's resources 🙈

VPCs are the reason why resources can be made private to you. You also get control over resources in a VPC, so you can organize how they communicate and integrate with each other without the public internet.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my account ever since my AWS account was created. This is because When you created your AWS account, AWS automatically sets up a default VPC for you! This default VPC is why you could launch resources (e.g. EC2 instances) and connect services together from Day 1 of using AWS. If it didn't exist, you would've had to learn how to create a VPC before you can use some of the services that need VPCs to function.

This default VPC is a handy starting point, especially for beginners, but you can always create custom VPCs to fit specific requirements e.g. strict security measures.

![Virtual Private Clouds (VPCs)](https://nextwork.ai/intense_gray_jolly_kokako/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_2facf927)

### Defining IPv4 CIDR blocks

To set up my VPC, I had to define an IPv4 CIDR block, which is (Classless Inter-Domain Routing) is a way to assign a whole block of IP addresses, kind of like creating a zone/area in a city.

## Subnets

### What I did in this step

In this step, I will We've created our VPC, which is like setting up a brand new city in your AWS Region.

Our new city is just a big open space until we organize it into different neighborhoods or areas. Your next step is to divide this large space into subdivisions called subnets, so you can start planning where different resources will live and operate.

### Creating and configuring subnets

Subnets are like different neighborhoods inside your city. You use subnets to group resources with similar access rules and restrictions. There are already subnets existing in my account, The default VPC in your account comes with predefined subnets in each Availability Zone of a Region, which means you'll see 3 subnets on your page if your Region has 3 Availability Zones

### Public vs private subnets

The difference between public and private subnets are

A public subnet is connected to the internet 🌐 Resources inside a public subnet can communicate with external networks.

A private subnet does not have direct internet access 🔐 You'd use it for internal resources that don’t need to be publicly accessible.

For a subnet to be considered public, it has to have a connection to  internat gateway .

![Subnets](https://nextwork.ai/intense_gray_jolly_kokako/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_157c4219)

### Auto-assigning public IPv4 addresses

Once I created my subnet, I enabled auto-assign public IPv4 addresses. When you enable auto-assign public IPv4 address for a subnet, any EC2 instance launched in that subnet will instantly get a public IP address so you won't have to create one manually - a huge time saver!

## Internet gateways

### What I did in this step

In this step, I will create a Internet gateway

Time for the last step in this project - let's attach your VPC with an internet gateway. This is like building a bridge (internet gateway) that links your private city (VPC) to the outside world (the internet), so your resources can communicate beyond your private space.

### Setting up internet gateways

An internet gateway connects your city (VPC) and the outside world (internet).

Internet gateways are key to making applications available on the internet. By attaching an internet gateway, your instances can access the internet and be accessible to external users.

Attaching an internet gateway means resources in your VPC can now access the internet. The EC2 instances with public IP addresses also become accessible to users, so your applications hosted on those servers become public too.

![Internet gateways](https://nextwork.ai/intense_gray_jolly_kokako/uploads/7f907ac7-2473-5c15-a8be-edb36581cdba_4ae90410)

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will Launch a VPC in Seconds with AWS CloudShell because we will use the AWS CLI to launch your VPC's resources and report back on whether it was a faster, more efficient way to do this project.

### Exploring CloudShell and CLI

VPC resources could also be created with CloudShell. AWS CloudShell is shell in your AWS Management Console, which means it's a space for you to run code. The awesome thing about AWS CloudShell is that it already has AWS CLI pre-installed.

AWS CLI (Command Line Interface) is a software that lets you create, delete and update AWS resources with commands instead of clicking through your console.

### Debugging my setup

To set up a VPC or a subnet, you can use the below command.\
To Crete a VPC :\
aws ec2 create-vpc --cidr-block 10.0.0.0/24 --query Vpc.VpcId --output text\
To Crete a subnet \
aws ec2 create-subnet --vpc-id VPC-ID --cidr-block ADD-CIDR-BLOCK-HERE

Make sure to avoid errors by including correct CIDR .

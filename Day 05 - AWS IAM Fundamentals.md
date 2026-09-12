# Day 05 - AWS IAM Fundamentals....

## What is IAM?

AWS IAM stands for Identity and Access Management...

IAM is used to securely control who can access AWS resources and what actions they can perform.

## Main Components of IAM.....

### 1. IAM User

An IAM User represents a person or application that needs access to AWS resources.

Example:

A DevOps engineer may have an IAM user with permission to manage EC2 and S3.

### 2. IAM Group

A Group is a collection of IAM users.

Example:

Create a DevOps group and assign required permissions to all DevOps engineers.

### 3. IAM Policy

A Policy is a JSON document that defines permissions.

Example:

A policy can allow a user to:

- Start and stop EC2 instances
- Read objects from S3
- Create CloudWatch logs

### 4. IAM Role

An IAM Role provides temporary permissions to AWS services or users.

Example:

An EC2 instance can use an IAM Role to access S3 without storing AWS access keys on the server.

## IAM Best Practices

- Follow the principle of least privilege
- Avoid using the root account for daily work
- Enable MFA
- Use IAM Roles for AWS services
- Avoid hardcoding access keys
- Give users only the permissions they need
- Regularly review unused permissions

## Real-World DevOps Example

Suppose an application is running on an EC2 instance and needs to download files from S3.

Instead of storing AWS access keys inside the EC2 server, we can:

1. Create an IAM Role
2. Attach an S3 policy to the role
3. Attach the role to the EC2 instance
4. The application can access S3 securely

This improves security because we don't need to store permanent credentials on the server.

## Important Interview Question

### Why should we use IAM Roles instead of Access Keys?

IAM Roles provide temporary credentials and avoid storing permanent access keys on servers.

For AWS services like EC2, Lambda, and ECS, using IAM Roles is a more secure approach.

## What I Learned Today

- IAM Users
- IAM Groups
- IAM Policies
- IAM Roles
- Least Privilege
- MFA
- Secure AWS access
- IAM Role with EC2 and S3

## Day 05 Completed

Continuing my 90 Days DevOps Challenge by learning AWS security and access management step by step.

#AWS #IAM #AWSCloud #DevOps #CloudComputing #90DaysDevOpsChallenge

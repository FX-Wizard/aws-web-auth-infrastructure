# Cognito-ALB Integration with CloudFormation


## Overview
Make your web app public with SSL/TLS and user authentication through Amazon Cognito


## What Does This Deploy
There are 2 templates in this repo.

1. Deploys a Cognito User Pool to manage users. If you already have a Cognito User Pool you can skip this and just deploy the 2nd stack.

2. Deploys an Application Load Balancer (ALB) and associated infrastructure to authenticate traffic and forward to the web server.

![Architecture Diagram](./diagrams/Cognito%20ALB.png)

## Prerequisites
- EC2 instance to point the ALB at, this can be in a private subnet.
- Some public subnets in your VPC for the ALB to live in.
- A domain name with a Route53 hosted zone set up.


## How To Deploy

1. Use Cloudformation to deploy the `cf-cognito-user-pool.yaml` template.

2. Once finished if you have not done so yet, go to the AWS Console and open Cognito and add some users.

3. Deploy `cf-alb-cognito.yaml`.

4. Once deployed, assign the security group to the EC2 instance.


## Clean Up

If you don't need this stack anymore simply delete it using the AWS Console Cloudformation page.

Or you can use the CLI, replacing the stack name with whatever you named the stacks.
```bash
aws cloudformation delete-stack --stack-name cognito-alb-stack
```


## To Do

Have the EC2 instance turn on/off when a cognito user logs in/out 
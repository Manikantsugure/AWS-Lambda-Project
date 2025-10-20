AWS Lambda EC2 Auto Start/Stop
Project Overview

This project demonstrates how to automatically stop and start Amazon EC2 instances at scheduled intervals using AWS Lambda and Amazon EventBridge. Automating EC2 management helps reduce costs and ensures resources run only when needed.

Features

Automatically stop EC2 instances to save costs.

Automatically start EC2 instances at scheduled times.

Monitor EC2 instance status.

Schedule tasks using AWS EventBridge rules.

Fully serverless solution using AWS Lambda.

Prerequisites

AWS Account with permissions to create IAM roles, Lambda functions, EC2 instances, and EventBridge rules.

Basic knowledge of Python or Node.js for Lambda scripting.

Installed AWS CLI (optional, for testing locally).

Steps to Implement
1. Create IAM Role & Policy

Create a custom IAM policy with permissions to:

ec2:StartInstances

ec2:StopInstances

ec2:DescribeInstances

Attach the policy to a Lambda execution role.

2. Create Lambda Functions

Lambda function to stop EC2 instances:

import boto3

ec2 = boto3.client('ec2')

def lambda_handler(event, context):
    ec2.stop_instances(InstanceIds=['i-0123456789abcdef0'])
    return 'Stopped EC2 instance'


Lambda function to start EC2 instances:

import boto3

ec2 = boto3.client('ec2')

def lambda_handler(event, context):
    ec2.start_instances(InstanceIds=['i-0123456789abcdef0'])
    return 'Started EC2 instance'


Replace InstanceIds with your EC2 instance IDs.

3. Test Lambda Functions

Test manually from the Lambda console to ensure EC2 instances start and stop correctly.

4. Create EventBridge Rules

Create two EventBridge rules:

Rule 1: Triggers Lambda to stop EC2 at a specific time.

Rule 2: Triggers Lambda to start EC2 at a specific time.

Schedule using cron expressions (e.g., daily at 9 PM).

5. Check EC2 Status

You can verify the state of EC2 instances via:

AWS Console → EC2 → Instances

Lambda logs in CloudWatch

Folder Structure
aws-ec2-lambda-automation/
│
├─ stop_ec2_lambda.py
├─ start_ec2_lambda.py
├─ README.md
└─ iam_policy.json

Screenshots (Optional)

Include screenshots of:

Lambda function setup

EventBridge rule configuration

EC2 instance status before/after execution

Benefits

Saves AWS costs by automating instance usage.

Fully serverless – no need for cron jobs on local machines.

Easy to customize schedules as per project requirements.

References

AWS Lambda Documentation

Amazon EventBridge Documentation

Automate EC2 Start/Stop Using Lambda

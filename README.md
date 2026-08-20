# 🚀 Serverless EC2 Scheduler

A serverless AWS automation project that automatically starts and stops EC2 instances using **AWS Lambda** and **Amazon EventBridge Scheduler**.

## 🎯 Project Goal

The goal of this project is to automate EC2 instance management and help reduce unnecessary AWS cloud costs.

### Real-World Use Case

- 🌙 Stop development servers at night
- ☀️ Start development servers in the morning
- 💰 Reduce unnecessary EC2 running costs
- 🏷️ Dynamically target instances using EC2 tags

---

## 🏗️ Architecture

Amazon EventBridge Scheduler
            ↓
        AWS Lambda
            ↓
     EC2 Instances
            ↓
    AutoSchedule=true

---

☁️ AWS Services Used
- Amazon EC2 – Compute instances
- AWS Lambda – Serverless automation
- Amazon EventBridge Scheduler – Scheduled execution
- AWS IAM – Least privilege permissions

---

## 🔐 IAM Least Privilege

The Lambda execution role uses least privilege permissions.

### Allowed Permissions

- ec2:DescribeInstances
- ec2:StartInstances
- ec2:StopInstances

Start and stop permissions are restricted to EC2 instances with:

AutoSchedule=true

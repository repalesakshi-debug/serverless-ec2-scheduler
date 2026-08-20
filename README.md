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

---

🏷️ EC2 Tagging

The EC2 instances are tagged with:

Key	Value
AutoSchedule	true

Lambda dynamically identifies EC2 instances using this tag instead of hardcoding instance IDs.

---

⚡ AWS Lambda

The Lambda function receives an action from the scheduler:

Start
{
  "action": "start"
}
Stop
{
  "action": "stop"
}

The Lambda function:

- Finds EC2 instances with AutoSchedule=true
- Collects their instance IDs
- Starts or stops the instances
- Returns the execution result

  ---
  
🔐 IAM Least Privilege

The Lambda execution role is configured with limited EC2 permissions.

Permissions
- ec2:DescribeInstances
- ec2:StartInstances
- ec2:StopInstances

Start and stop permissions are restricted to instances with:

AutoSchedule=true

This follows the Principle of Least Privilege.

---

⏰ EventBridge Schedules
- 🛑 Stop Scheduler

Runs at 8:00 PM and stops the tagged EC2 instances.

- ▶️ Start Scheduler

Runs at 8:00 AM and starts the tagged EC2 instances.

---

📂 Project Structure
serverless-ec2-scheduler/
│
├── README.md
├── lambda_function.py
├── iam-policy.json
│
├── events/
│   ├── start-event.json
│   └── stop-event.json
│
└── screenshots/

---

📸 Project Screenshots

- EC2 Tag

- IAM Role

- IAM Policy

- Lambda Function

- Lambda Start Test

- Lambda Stop Test

- EventBridge Stop Scheduler

- EventBridge Start Scheduler

- EC2 Status

  ---

🚀 Benefits
- Serverless automation
- Automated EC2 management
- Cost optimization
- Tag-based resource targeting
- IAM least privilege
- No hardcoded EC2 instance IDs

  ---
  
🧠 Skills Demonstrated

AWS | EC2 | Lambda | EventBridge Scheduler | IAM | Python | Serverless Architecture | Cloud Automation | Cost Optimization

## 🏗️ Architecture
```text
   Amazon EventBridge Scheduler
            ↓
     AWS Lambda
            ↓
    EC2 Instances
            ↓
    AutoSchedule=true

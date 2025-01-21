# ☁️ **AWS Deployment Cheat Sheet for Machine Learning & Data Engineers**

---

## 🎯 **Overview**
This cheat sheet provides a step-by-step guide for deploying ML models and data pipelines using AWS, focusing on key services and configurations.

---

## 🛠 **AWS Website Steps for Deployment**

### 1️⃣ **Set Up Your AWS Account**
- **Create an AWS Account:**
  1. Visit [AWS Registration](https://aws.amazon.com/).
  2. Sign up using your email and payment details.
- **Activate Free Tier:**
  - Utilize free-tier services to reduce initial costs.

---

### 2️⃣ **Create an IAM Role**
- **Navigate to IAM:**
  1. Go to **IAM** service from the AWS Management Console.
  2. Select **Roles** → **Create Role**.
- **Choose Trusted Entity:**
  - Select **AWS Service**.
- **Assign Policies:**
  - Attach policies such as `AmazonS3FullAccess`, `AmazonEC2FullAccess`, or custom policies.
- **Role Name:**
  - Assign a meaningful name (e.g., `ml-deployment-role`).

---

### 3️⃣ **Set Up S3 Bucket**
- **Navigate to S3:**
  1. Go to **S3** service.
  2. Click **Create Bucket**.
- **Configure the Bucket:**
  - Name: Use a unique name (e.g., `ml-model-deployment`).
  - Region: Choose a region close to your users.
  - Permissions: Enable/disable public access as needed.
- **Upload Files:**
  - Upload model artifacts, datasets, or other necessary files.

---

### 4️⃣ **Launch an EC2 Instance**
- **Navigate to EC2:**
  1. Go to **EC2** service.
  2. Click **Launch Instance**.
- **Choose AMI:**
  - Select **Deep Learning AMI** or Ubuntu.
- **Select Instance Type:**
  - Choose GPU-enabled instances (e.g., `g4dn.xlarge`) for ML workloads.
- **Configure Instance:**
  - Attach IAM Role created earlier.
  - Add storage as needed.
- **Launch and Connect:**
  - Launch the instance and connect via SSH.

---

### 5️⃣ **Set Up Elastic Beanstalk for Web Apps**
- **Navigate to Elastic Beanstalk:**
  1. Go to **Elastic Beanstalk**.
  2. Click **Create New Application**.
- **Choose Environment:**
  - Select **Web Server Environment**.
- **Upload Application Code:**
  - Upload your code packaged in `.zip` or `.war` format.
- **Configure Resources:**
  - Set instance type, load balancer, and scaling.
- **Deploy:**
  - Click **Deploy** and monitor health status.

---

### 6️⃣ **Set Up Lambda for Serverless Deployment**
- **Navigate to Lambda:**
  1. Go to **AWS Lambda**.
  2. Click **Create Function** → **Author from Scratch**.
- **Configure the Function:**
  - Choose runtime (e.g., Python 3.8).
  - Attach IAM Role for permissions.
- **Upload Code:**
  - Package code and dependencies into a `.zip` file.
  - Upload via the console or S3.
- **Configure Triggers:**
  - Add triggers such as API Gateway or S3 events.

---

### 7️⃣ **Set Up API Gateway**
- **Navigate to API Gateway:**
  1. Go to **API Gateway**.
  2. Create a new REST API.
- **Configure Resources:**
  - Define endpoints (e.g., `/predict`).
  - Link methods (e.g., POST) to Lambda functions or EC2 URLs.
- **Deploy API:**
  - Create a new stage (e.g., `prod`) and deploy.

---

### 8️⃣ **Monitor and Optimize**
- **Enable CloudWatch Logs:**
  - Track logs for EC2, Lambda, or API Gateway.
- **Set Up Alarms:**
  - Monitor CPU usage, memory, and request rates.
- **Auto-Scaling:**
  - Configure scaling policies for EC2 or Elastic Beanstalk.

---

## 🌟 **Best Practices**
- **Security:**
  - Restrict access using IAM policies.
  - Use secrets manager for sensitive data.
- **Cost Management:**
  - Set budget alerts in AWS Billing.
- **Automation:**
  - Use **CloudFormation** or **Terraform** for infrastructure as code.
- **Documentation:**
  - Document deployment steps and configurations.

---

🌐 **Happy AWS Deployments!** 🚀


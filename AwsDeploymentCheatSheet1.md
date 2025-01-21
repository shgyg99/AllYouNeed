# ☁️ **AWS Deployment Cheat Sheet for ML & Data Engineers**

---

## 🎯 **AWS Basics**

- **Log In to AWS:**
  Visit [AWS Management Console](https://aws.amazon.com/console/).

- **Install AWS CLI:**
  ```bash
  pip install awscli
  aws configure
  ```

- **Common CLI Commands:**
  ```bash
  aws s3 ls                # List S3 buckets
  aws ec2 describe-instances  # List EC2 instances
  aws lambda list-functions  # List Lambda functions
  ```

---

## 🗂 **S3 (Simple Storage Service)**

- **Create a Bucket:**
  ```bash
  aws s3 mb s3://<bucket_name>
  ```

- **Upload a File:**
  ```bash
  aws s3 cp <file_path> s3://<bucket_name>/
  ```

- **Download a File:**
  ```bash
  aws s3 cp s3://<bucket_name>/<file_name> <local_path>
  ```

- **Sync a Directory:**
  ```bash
  aws s3 sync <local_directory> s3://<bucket_name>/
  ```

- **Set Bucket Permissions:**
  ```bash
  aws s3api put-bucket-acl --bucket <bucket_name> --acl public-read
  ```

---

## 🖥 **EC2 (Elastic Compute Cloud)**

- **Launch an EC2 Instance:**
  ```bash
  aws ec2 run-instances \
    --image-id <ami_id> \
    --count 1 \
    --instance-type <instance_type> \
    --key-name <key_pair_name> \
    --security-group-ids <sg_id> \
    --subnet-id <subnet_id>
  ```

- **Connect to an EC2 Instance:**
  ```bash
  ssh -i <key_pair.pem> ec2-user@<public_ip>
  ```

- **Stop an Instance:**
  ```bash
  aws ec2 stop-instances --instance-ids <instance_id>
  ```

- **Terminate an Instance:**
  ```bash
  aws ec2 terminate-instances --instance-ids <instance_id>
  ```

---

## 🔄 **Lambda Functions**

- **Create a Lambda Function:**
  ```bash
  aws lambda create-function \
    --function-name <function_name> \
    --runtime <runtime> \
    --role <execution_role_arn> \
    --handler <file_name>.<handler> \
    --zip-file fileb://<deployment_package.zip>
  ```

- **Invoke a Function:**
  ```bash
  aws lambda invoke \
    --function-name <function_name> \
    --payload '<json_payload>' output.json
  ```

- **Update Function Code:**
  ```bash
  aws lambda update-function-code \
    --function-name <function_name> \
    --zip-file fileb://<deployment_package.zip>
  ```

---

## 📊 **SageMaker**

- **Train a Model:**
  ```python
  import sagemaker
  from sagemaker import get_execution_role

  role = get_execution_role()
  sess = sagemaker.Session()

  estimator = sagemaker.estimator.Estimator(
      image_uri='<image_uri>',
      role=role,
      instance_count=1,
      instance_type='ml.m5.large',
      output_path='s3://<bucket_name>/output/'
  )

  estimator.fit({'train': 's3://<bucket_name>/train/'})
  ```

- **Deploy a Model:**
  ```python
  predictor = estimator.deploy(
      initial_instance_count=1,
      instance_type='ml.t2.medium'
  )
  ```

- **Make Predictions:**
  ```python
  result = predictor.predict(data)
  print(result)
  ```

---

## 📦 **ECS (Elastic Container Service)**

- **Push Docker Image to ECR:**
  ```bash
  aws ecr create-repository --repository-name <repository_name>
  $(aws ecr get-login --no-include-email)
  docker tag <image_id> <ecr_uri>/<repository_name>:<tag>
  docker push <ecr_uri>/<repository_name>:<tag>
  ```

- **Deploy Service with ECS:**
  ```bash
  aws ecs create-service \
    --service-name <service_name> \
    --task-definition <task_definition> \
    --desired-count 1 \
    --cluster <cluster_name>
  ```

---

## 🔄 **CI/CD with CodePipeline**

- **Create a Pipeline:**
  ```bash
  aws codepipeline create-pipeline \
    --pipeline <pipeline_json_file>
  ```

- **View Pipeline Status:**
  ```bash
  aws codepipeline get-pipeline-state --name <pipeline_name>
  ```

- **Manually Start a Pipeline:**
  ```bash
  aws codepipeline start-pipeline-execution --name <pipeline_name>
  ```

---

## 🌐 **API Gateway**

- **Create a REST API:**
  ```bash
  aws apigateway create-rest-api --name <api_name>
  ```

- **Deploy an API Stage:**
  ```bash
  aws apigateway create-deployment \
    --rest-api-id <api_id> \
    --stage-name <stage_name>
  ```

- **Invoke an API Endpoint:**
  ```bash
  curl -X GET <endpoint_url>
  ```

---

## 🧹 **Clean Up Resources**

- **Delete an S3 Bucket:**
  ```bash
  aws s3 rb s3://<bucket_name> --force
  ```

- **Delete an EC2 Instance:**
  ```bash
  aws ec2 terminate-instances --instance-ids <instance_id>
  ```

- **Delete a Lambda Function:**
  ```bash
  aws lambda delete-function --function-name <function_name>
  ```

- **Delete an ECR Repository:**
  ```bash
  aws ecr delete-repository --repository-name <repository_name> --force
  ```

---

🌟 **Happy Deployments!** 🚀


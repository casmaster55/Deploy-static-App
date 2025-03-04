DEPLOY A STATIC WED APP ON AWS WITH DOCKER, AMAZON ECR, AND ECS

# 🚀 DEPLOY A STATIC WED APP ON AWS WITH DOCKER, AMAZON ECR, AND ECS

## 📝 Project Overview
This project demonstrates how to deploy a static web application on **AWS** using **Docker, Amazon Elastic Container Registry (ECR), and Amazon Elastic Container Service (ECS)**. The goal is to containerize the application, store the image in ECR, and deploy it to ECS for scalable cloud hosting.

---

## 🏗️ Technologies Used
- **AWS** (ECR, ECS, IAM, CloudWatch)
- **Docker** (Containerization)
- **Amazon Elastic Container Service (ECS)**
- **Amazon Elastic Container Registry (ECR)**
- **Amazon Application Load Balancer (ALB)**
- **AWS Fargate** (Serverless container execution)
- **GitHub Actions (Optional - for CI/CD)**

---

## 🚀 Project Setup & Deployment Steps

### **1️⃣ Clone the Repository**
```sh
git clone https://github.com/casmaster55/aws-docker-static-app.git
cd aws-docker-static-app

2️⃣ Create a Dockerfile

Inside your project folder, create a Dockerfile to containerize the static web app.
# Use Nginx as the base image
FROM nginx:alpine

# Copy the static website files to the Nginx HTML directory
COPY . /usr/share/nginx/html

# Expose port 80 for the web service
EXPOSE 80

# Start the Nginx server
CMD ["nginx", "-g", "daemon off;"]

3️⃣ Build and Test the Docker Image Locally


check http://localhost:8080 in your browser to confirm the app is running.

4️⃣ Set Up AWS CLI and Authenticate to ECR
Ensure AWS CLI is installed and configured.

Then, authenticate Docker to AWS ECR:
aws ecr create-repository --repository-name my-static-web-app

5️⃣ Create an Amazon ECR Repository
aws ecr describe-repositories

6️⃣ Tag and Push the Docker Image to ECR
docker tag my-static-web-app:latest <aws_account_id>.dkr.ecr.us-east-1.amazonaws.com/my-static-web-app
docker push <aws_account_id>.dkr.ecr.us-east-1.amazonaws.com/my-static-web-app

7️⃣ Deploy to Amazon ECS (Fargate)
aws ecs create-cluster --cluster-name my-cluster

Create a Task Definition with:
Image: ECR image URL
Port Mapping: 80
Memory & CPU: Configure based on app needs
Fargate launch type
Create a Service to run the task in ECS.
Attach an Application Load Balancer (ALB) to expose the service.



This project showcases the process of containerizing and deploying a static website using Docker, AWS ECR, and ECS (Fargate). By leveraging AWS services, the deployment is both scalable and cost-effective.

✅ Key Takeaways:

The static web application was containerized using Docker.
The container image was pushed to AWS Elastic Container Registry (ECR).
The application was deployed on AWS Elastic Container Service (ECS) with Fargate for serverless execution.



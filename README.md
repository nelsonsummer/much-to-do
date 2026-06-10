# Much-To-Do Application (CI/CD Enabled)

## Overview
This project is a full-stack task management application built with:
- Frontend: React (Vite)
- Backend: Go (Gin)
- Infrastructure: AWS (EC2, ALB, ASG, S3)
- CI/CD: GitHub Actions
- Containerization: Docker
- Infrastructure as Code: Terraform

---

## Architecture

- Frontend deployed to AWS S3
- Backend deployed on EC2 Auto Scaling Group behind an Application Load Balancer
- Terraform provisions all AWS resources
- GitHub Actions handles CI/CD automation

---

## CI/CD Pipelines

### Backend Pipeline
- Runs Go unit tests
- Builds Docker image
- Scans image with Trivy
- Deploys via AWS infrastructure

### Frontend Pipeline
- Installs dependencies
- Runs lint checks
- Builds React app
- Deploys to S3 bucket
- Invalidates CloudFront cache

---

## Docker

Backend is containerized:

```bash
docker build -t muchtodo-api .

Run container:

docker run -p 8080:8080 muchtodo-api

AWS Resources Used
EC2 Auto Scaling Group
Application Load Balancer
S3 Bucket (Frontend hosting)
IAM Roles for EC2
CloudWatch Logging
Deployment Flow
Push code to feature/full-stack
GitHub Actions triggers CI/CD pipelines
Backend builds and deploys Docker image
Frontend builds and syncs to S3
Terraform provisions infrastructure

Author
Submitted for AWS DevOps Assessment


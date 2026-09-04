🚀 Netflix Clone DevSecOps CI/CD Pipeline

A complete DevSecOps CI/CD project demonstrating automated application building, security scanning, containerization, deployment, and verification using Jenkins and AWS.

📌 Project Overview

This project implements a complete CI/CD pipeline for a Netflix Clone application.

The application is automatically:

Pulled from GitHub
Analyzed using SonarQube
Validated using SonarQube Quality Gate
Containerized using Docker
Scanned for vulnerabilities using Trivy
Pushed to Amazon ECR
Deployed to an AWS EC2 instance
Verified after deployment
🏗️ Architecture
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Jenkins Pipeline
    │
    ├── Checkout Source Code
    │
    ├── SonarQube Analysis
    │
    ├── Quality Gate
    │
    ├── Docker Build
    │
    ├── Trivy Security Scan
    │
    ├── Amazon ECR
    │
    ▼
AWS EC2 Deployment
    │
    ▼
Netflix Clone Application
🛠️ Technologies Used
Technology	Purpose
GitHub	Source Code Management
Jenkins	CI/CD Automation
SonarQube	Code Quality Analysis
Docker	Application Containerization
Trivy	Container Security Scanning
AWS EC2	Application Hosting
Amazon ECR	Docker Image Registry
AWS CLI	AWS Service Integration
SSH Agent	Secure EC2 Deployment
🔄 Jenkins Pipeline Stages
1. Checkout Source Code

Jenkins automatically retrieves the application source code from GitHub.

GitHub → Jenkins
2. Check Project Files

The pipeline verifies the repository structure and application files.

3. SonarQube Analysis

The application source code is analyzed using SonarQube.

This helps identify:

Code quality issues
Bugs
Security vulnerabilities
Code smells
4. Quality Gate

Jenkins waits for the SonarQube Quality Gate result.

The pipeline continues only when the configured quality requirements are satisfied.

5. Docker Build

The Netflix Clone application is containerized using Docker.

Docker Image:

netflix-clone:latest

The TMDB API key is securely provided through Jenkins Credentials during the Docker build.

6. Trivy Image Scan

The Docker image is scanned using Trivy for security vulnerabilities.

The scan checks for:

HIGH vulnerabilities
CRITICAL vulnerabilities
7. Amazon ECR Login

Jenkins authenticates with Amazon Elastic Container Registry using AWS CLI.

8. Docker Image Tagging

The Docker image is tagged for the Amazon ECR repository.

netflix-clone-devsecops:latest
9. Push Image to Amazon ECR

The Docker image is pushed to Amazon ECR.

Jenkins
   │
   ▼
Docker Image
   │
   ▼
Amazon ECR
10. Deploy to AWS EC2

Jenkins connects securely to the Application EC2 instance using SSH.

The deployment process:

Logs in to Amazon ECR
Pulls the latest Docker image
Stops the old container
Removes the old container
Starts the new container

The application container runs on:

Port 80
11. Verify Deployment

After deployment, Jenkins verifies that the application is accessible.

http://APPLICATION_IP
🔐 Jenkins Credentials Used

The following credentials are configured securely in Jenkins:

Credential ID	Purpose
TMDB_API_KEY	TMDB API Authentication
sonarqube-token	SonarQube Authentication
application-ec2-ssh-key	SSH Access to Application EC2

Sensitive credentials are not stored directly in the source code.

☁️ AWS Services Used
Amazon EC2

Used to host:

Jenkins
Application server
Amazon ECR

Used to store Docker container images.

📦 Application Deployment

The deployed application is accessible through the EC2 Public IP address.

http://18.61.255.197
🎯 CI/CD Workflow
GitHub
   │
   ▼
Jenkins
   │
   ├── SonarQube Analysis
   │
   ├── Quality Gate
   │
   ├── Docker Build
   │
   ├── Trivy Scan
   │
   ├── Push to Amazon ECR
   │
   ▼
AWS EC2
   │
   ▼
Docker Container
   │
   ▼
Netflix Clone Application
🐳 Docker Container

The application runs inside a Docker container.

docker run -d \
  --name netflix-application \
  -p 80:80 \
  netflix-clone:latest
📊 Project Features

✅ Automated CI/CD Pipeline
✅ Code Quality Analysis
✅ SonarQube Quality Gate
✅ Docker Containerization
✅ Container Security Scanning
✅ Amazon ECR Integration
✅ Automated EC2 Deployment
✅ SSH-Based Deployment
✅ Automated Deployment Verification

👨‍💻 Author

Varadharaj S

DevOps & Cloud Enthusiast

⭐ Project Status

🟢 Completed Successfully

The Netflix Clone application has been successfully deployed using a complete DevSecOps CI/CD pipeline.

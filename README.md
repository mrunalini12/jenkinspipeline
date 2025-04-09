CI/CD Pipeline using Jenkins, Docker, and GitHub Webhook
This project sets up a CI/CD pipeline using Jenkins, Docker, and GitHub Webhooks. It builds a basic HTML app, tests it, builds a Docker image, and deploys it as a running container. The Jenkins pipeline is automatically triggered using GitHub webhooks.

🔧 Tools & Technologies
Jenkins – For automation and pipeline creation

Docker – For containerizing the application

GitHub – Source code and webhook triggering

GitHub Webhook – For auto-triggering Jenkins on every push

Nginx – Base image for serving static files

📁 Files in the Project
index.html – Simple HTML file to serve

Dockerfile – Builds a Docker image with Nginx and copies the HTML

Jenkinsfile – Contains CI/CD pipeline logic

📜 Jenkinsfile Pipeline Stages
groovy
Copy
Edit
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker build -t jenkins-cicd-app .'
                sh 'docker run -d -p 8080:80 jenkins-cicd-app'
            }
        }
    }
}
🐳 Dockerfile
Dockerfile
Copy
Edit
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
This Dockerfile uses an Alpine-based Nginx image and serves a static HTML page.

🔔 GitHub Webhook Setup
Go to your GitHub repo → Settings → Webhooks

Click “Add Webhook” and enter:

Payload URL: http://<your-public-ip>:8080/github-webhook/

Content type: application/json

Event: Just the Push event

Save the webhook

⚙️ Jenkins Configuration
In your Jenkins job:

Under Build Triggers, check: ✅ GitHub hook trigger for GITScm polling

Make sure Jenkins is reachable via the public IP used in the webhook.

🐋 (Optional) Push Docker Image to Docker Hub
bash
Copy
Edit
docker tag jenkins-cicd-app mrunalini01/jenkins-cicd-app
docker push mrunalini01/jenkins-cicd-app
✅ Final Result
Jenkins pipeline runs automatically on GitHub push

Docker image is built and deployed

App is served at http://<your-ip>:8080 using Nginx


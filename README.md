# Jenkins CI/CD Pipeline with Docker

This project demonstrates a complete CI/CD pipeline using Jenkins, GitHub, Docker, and basic HTML content. The pipeline automates the build, test, and deploy stages, and finally runs the Docker container.

## 🔧 Tools Used

- **Jenkins**
- **GitHub**
- **Docker**
- **Ngrok** (for webhook testing)

---

## 📁 Repository Structure

├── Dockerfile ├── Jenkinsfile └── index.html


- `index.html`: A sample frontend file for deployment.
- `Dockerfile`: Builds a simple NGINX-based container to serve the HTML.
- `Jenkinsfile`: Contains the pipeline script with build, test, and deploy stages.

---

## ⚙️ Jenkins Pipeline Stages

### 1. **Build**
- Creates a Docker image using the `Dockerfile`.

### 2. **Test**
- Echo test stage (can be replaced with actual tests).

### 3. **Deploy**
- Runs the container locally to serve the application.
- Docker image is optionally pushed to Docker Hub.

---

## 🐳 Docker Hub

Image is pushed to [Docker Hub](https://hub.docker.com/u/mrunalini01):

```bash
docker login
docker tag jenkins-cicd-app mrunalini01/ci-cd-node-app
docker push mrunalini01/ci-cd-node-app

🔗 GitHub Webhook Integration
Webhook configured to trigger Jenkins on every push.

Used Ngrok to expose Jenkins running locally:

yaml
Copy
Edit
ngrok http 8080
Webhook URL added to GitHub:

perl
Copy
Edit
http://<your-ngrok-url>/github-webhook/
Note: Jenkins trigger via webhook was tested but skipped in final setup due to network/firewall issues. Manual build works fine.

✅ How to Run
Clone the repo.

Setup Jenkins job with GitHub repo.

Add Jenkinsfile path.

Run the job manually or configure webhook.

View the app on http://localhost:8080.

📦 Output
Docker container running NGINX serving index.html.

Image pushed to Docker Hub.

Logs in Jenkins for all stages (build, test, deploy).

👩‍💻 Author
Mrunalini
GitHub: @mrunalini12
Docker Hub: mrunalini01




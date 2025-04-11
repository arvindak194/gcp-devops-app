#  GCP DevOps CI/CD Project

This is a **Node.js + Express** web app deployed using a full **CI/CD DevOps pipeline** on **Google Cloud Platform (GCP)** — entirely for free using Cloud Shell and the GCP free tier.

![GCP](https://img.shields.io/badge/Platform-Google%20Cloud-blue)
![Cloud Run](https://img.shields.io/badge/Deployed%20On-Cloud%20Run-green)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Google%20Cloud%20Build-yellow)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 🌐 Live Demo

🔗 [https://devops-app-wbwcnmcg5a-el.a.run.app/](https://devops-app-wbwcnmcg5a-el.a.run.app/)  
> Displays: **"Hello from CI/CD Cloud Build"**

---

## 📦 Tech Stack

- **Node.js + Express** – Web app
- **Docker** – Containerized app
- **GitHub** – Source code + triggers
- **Cloud Build** – CI/CD
- **Artifact Registry** – Docker image storage
- **Cloud Run** – Serverless deployment
- **Cloud Shell** – All tools used for free

---

## ⚙️ CI/CD Pipeline (Automated Deployment)

1. ✅ **Push to `main` on GitHub**
2. ⚙️ **Cloud Build** triggers:
   - Build Docker image
   - Push to Artifact Registry
   - Deploy to Cloud Run
3. 🌍 **App is live instantly** on HTTPS

---

## 🗂️ File Structure

gcp-devops-app/ ├── index.js # Simple Express server ├── Dockerfile # Container instructions ├── cloudbuild.yaml # CI/CD pipeline config ├── package.json └── README.md


---

## 🧪 Local Development

```bash
# Install dependencies
npm install

# Start app
npm start
App will run at http://localhost:8080

---

📄 cloudbuild.yaml

steps:
  - name: 'gcr.io/cloud-builders/docker'
    args: ['build', '-t', 'asia-south1-docker.pkg.dev/$PROJECT_ID/devops-repo/devops-app', '.']
  - name: 'gcr.io/cloud-builders/docker'
    args: ['push', 'asia-south1-docker.pkg.dev/$PROJECT_ID/devops-repo/devops-app']
  - name: 'gcr.io/google.com/cloudsdktool/cloud-sdk'
    entrypoint: gcloud
    args:
      - run
      - deploy
      - devops-app
      - --image=asia-south1-docker.pkg.dev/$PROJECT_ID/devops-repo/devops-app
      - --region=asia-south1
      - --platform=managed
      - --allow-unauthenticated


Author
Arvind T
GitHub: @arvindak194


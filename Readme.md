# SIT737 - Cloud Native Application Development
## Practical Task 5D - Containerization and Docker Image Deployment

**Author:** Mitali Kaur  
**Deakin ID:** s224582251  
**GitHub Repository:** [https://github.com/Mita22-1/sit737-2025-prac5d](https://github.com/Mita22-1/sit737-2025-prac5d)

---

## Task Overview

In this task, we:
- Containerized a Node.js calculator web application
- Built the Docker image locally
- Pushed the Docker image to **Google Cloud Artifact Registry**

---

## Prerequisites

- Google Cloud SDK (`gcloud`)
- Docker installed and running
- Python installed (required by `gcloud`)
- Node.js installed
- Google Cloud Project created

---

## Steps Performed

### 1. Clone the Repository

git clone https://github.com/Mita22-1/sit737-2025-prac5d.git
cd sit737-2025-prac5d

### 2. Authenticate with Google Cloud

gcloud auth login
gcloud config set project sit737-25t1-mitali-kau-0aeda9f

### 3. Enable Artifact Registry API

gcloud services enable artifactregistry.googleapis.com

### 4. Create Docker Repository on Google Cloud

gcloud artifacts repositories create sit737-2025-prac5d \
  --repository-format=docker \
  --location=australia-southeast1 \
  --description="Docker repository" \
  --project=sit737-25t1-mitali-kau-0aeda9f

### 5. Build and Tag Docker Image

docker build -t australia-southeast1-docker.pkg.dev/sit737-25t1-mitali-kau-0aeda9f/sit737-2025-prac5d/calculator-app:latest .

### 6. Configure Docker Authentication

gcloud auth configure-docker australia-southeast1-docker.pkg.dev

### 7. Push Docker Image to Artifact Registry

docker push australia-southeast1-docker.pkg.dev/sit737-25t1-mitali-kau-0aeda9f/sit737-2025-prac5d/calculator-app:latest

# Student-Project-Tracker Web APP
A simple FastAPI web application for registering students and tracking their weekly progress during the Cloud Native Series.

### Key Features:
- Register new students (generates a unique ID).
- Track weekly progress for each student.
- All students use one central MongoDB (hosted on MongoDB Atlas or similar).
- Simple endpoints for registration, status check, and progress update.

## 📦 Prerequisites
- Python 3.10+ & Pip  
- Git
- MongoDB Atlas account (to get your connection string)
- Docker 
- Kubernetes (kubectl, kind) 

---

## 💻 Local Development Setup

### 1. Clone the Repository
```bash
git clone https://github.com/chisomjude/student-project-tracker.git
cd student-project-tracker
```

### 2. Create Virtual Environment & Install Dependencies
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
pip install -r requirements.txt
```

### 3.Db Connections
- navigate to app/main and update vault IP:

```
   export VAULT_ADDR=""
   export VAULT_ROLE_ID=""
   export VAULT_SECRET_ID="
```

### 4. Run the Application Locally
```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```
Visit `http://vmip:8000` to see your app in action.

---

## 🐳 Docker Instructions

### 1. Build Docker Image
```bash
docker build -t <image-name> .
```

### 2. Run Docker Container
```bash
docker run --env-file .env -p 8000:8000 <image-name>
```

### 3. Push to Docker Hub
Ensure you're logged in:
```bash
docker login
```
Tag and push your image:
```bash
docker tag student-tracker your-dockerhub-username/student-tracker

docker push your-dockerhub-username/student-tracker
```

---

## 📬 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | `/register?name=YourName` | Register new student |
| GET    | `/status/{student_id}`    | View registration and progress |
| POST   | `/update/{student_id}?week=week1` | Update progress by week |

---

<!--## 🌐 Deploying to Cloud (Optional)
You can deploy the app on platforms like:
- Render
- Railway
- Fly.io
- Azure App Service
- Elastic Beanstalk or more-->

---
## Cloud Native Project Schedule

| Week | Topic                                          | Learning Goals                                    | Hands-on Project                                            |
| ---- | ---------------------------------------------- | ------------------------------------------------- | ----------------------------------------------------------- |
| 1    | **Intro to Cloud Native & Environment Setup**  | CNCF, containers, microservices, what we'll build | Set up cloud-based workstation, install Docker, Git, Python |
| 2    | **Containerization with Docker**               | Dockerfile, build/push/run containers             | Containerize FastAPI app, push to DockerHub                 |
| 3    | **Intro to Kubernetes with Kind**              | Pods, Services, Deployments, kubeconfig           | Install Kind, deploy app on local cluster                   |
| 4    | **Helm Basics & Chart Templates**              | Helm chart structure, values, reuse               | Create Helm chart for app, deploy with Helm                 |
| 5    | **Kubernetes Services & Ingress**              | LoadBalancer, NodePort, Ingress Controller        | Add Ingress to access app externally (e.g., NGINX Ingress)  |
| 6    | **GitHub Actions for CI/CD**                   | Docker build & Helm release pipeline              | Set up Actions to build/push image & update Helm chart      |
| 7    | **GitOps with ArgoCD**                         | GitOps concepts, ArgoCD installation              | Install ArgoCD on Kind, sync Helm app from GitHub           |
| 8    | **App Configs, Secrets, and Envs**             | K8s secrets/configmaps, secure deployment         | Refactor app to use secrets/configmaps, update Helm         |
| 9    | **Monitoring with Prometheus & Grafana**       | Metrics, dashboards, K8s monitoring stack         | Install Prometheus/Grafana with Helm, monitor app health    |
| 10   | **Logging & Observability with Loki**          | Collect app logs, visualize in Grafana            | Install Loki, tail app logs in Grafana                      |
| 11   | **Scaling, Resource Limits, and Auto-healing** | HPA, readiness/liveness probes                    | Add CPU/memory limits, HPA for app                          |
| 12   | **Capstone Review & Portfolio Setup**          | Recap full pipeline, deploy final version         | Students demo full CI/CD + GitOps + Observability setup     |


<!--## 👩🏽‍💻 Built for the Cloud Native Series by Chisom
This project is used for learning cloud-native tools and Hands-on Project.

Feel free to fork and extend it! ->

#  DevOps Assessment Assignment

Tool & Experience Self-Assessment
<img width="766" height="648" alt="image" src="https://github.com/user-attachments/assets/723ee527-afeb-48b5-a44c-3f07741bc3d6" />

##  Overview

This project demonstrates a **complete DevOps workflow** for a microservice-based application, including:

* Containerization (Docker)
* CI/CD (GitHub Actions)
* Infrastructure as Code (Terraform)
* Cloud deployment (AWS ECS, S3, ALB)
* Monitoring (Amazon Managed Prometheus + Grafana + CloudWatch)

---

##  Architecture

###  High-Level Flow

User → S3 (Frontend) → ALB → ECS (Backend + Worker) → Redis (ElastiCache)
↓
Monitoring (AMP + Grafana + CloudWatch)

---

##  Key Components

###  Backend (`backend/main.py`)

* FastAPI application
* `POST /notify/` → triggers background task
* `GET /task_status/{task_id}` → fetch task status

---

###  Worker (`backend/worker.py`)

* Celery worker
* Executes async tasks

---

###  Redis (ElastiCache)

* Message broker
* Result backend

---

###  Frontend (`frontend/index.html`)

* Single-page UI
* Triggers task
* Polls backend for status

---

##  Containerization

* Backend and worker containerized using Docker
* Multi-service setup using docker-compose

###  Environment Variables

All hardcoded values replaced with env variables:

```env
REDIS_URL
API_BASE_URL
AWS_REGION
```

---

##  Run Locally (Docker)

###  Build Images

```bash
docker-compose build
```

---

###  Start Full Stack

```bash
docker-compose up
```

---

###  Access Services

* Frontend → http://localhost:3000
* Backend → http://localhost:8000/docs
* Prometheus → http://localhost:9090
* Grafana → http://localhost:3001

---

###  View Logs

```bash
docker-compose logs -f
```

---

##  Cloud Deployment (AWS)

###  Infrastructure (Terraform)

Provisioned resources:

* ECS Fargate (Backend + Worker)
* Application Load Balancer (ALB)
* S3 (Frontend hosting)
* ElastiCache (Redis)
* ECR (Docker images)
* IAM Roles & Security Groups

---

###  Deploy Infra

```bash
cd infra/backend
terraform init
terraform apply
```

---

##  CI/CD Pipeline (GitHub Actions)

### Backend Pipeline

* Lint (flake8)
* Test (basic validation)
* Build Docker image
* Security scan (Trivy)
* Push to ECR
* Deploy to ECS

---

### Frontend Pipeline

* Upload static files to S3
* Auto-deploy on push

---

##  Monitoring & Observability

###  Metrics Pipeline

App → ADOT → Amazon Managed Prometheus → Grafana

---

###  Tools Used

* Amazon Managed Prometheus (AMP)
* Amazon Managed Grafana (AMG)
* CloudWatch (ECS metrics & logs)

---

###  Dashboard Includes

* App health (`up`)
* Request rate
* Total requests
* Latency
* ECS CPU & Memory
* Service health

---

##  Project Structure

```bash
.
├── backend/
├── frontend/
├── infra/
│   ├── backend/
│   ├── frontend/
├── .github/workflows/
├── docker-compose.yml
├── Dockerfile
├── prometheus.yml
└── README.md
```

---

##  Deliverables

*  Containerized application
*  Infrastructure as Code (Terraform)
*  CI/CD pipeline
*  Monitoring setup
*  Production-ready deployment
*  Architecture diagram

---

##  Key Highlights

* Fully automated CI/CD pipeline
* Zero manual deployment
* Scalable ECS-based architecture
* Managed AWS services used wherever possible
* End-to-end observability implemented

---

##  Future Improvements

* Auto-scaling ECS services
* Alerting (CPU, failures)
* CloudFront + HTTPS
* Blue/Green deployments

---

##  Author

Suhas Podey

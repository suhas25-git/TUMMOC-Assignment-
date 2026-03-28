# Local Setup Instructions

This document explains how to run the application locally using Docker.

---

## Prerequisites

Ensure the following tools are installed on your system:

* Docker
* Docker Compose
* Git

---

## Clone the Repository

```bash
git clone <repo-url>
cd devops-assignment
```

---

## Run the Application Locally

### Build and Start Services

```bash
docker compose up --build
```

This command will start the following services:

* Backend API → http://localhost:8000
* Frontend → http://localhost:3000
* Redis (message broker)
* Celery worker (background processing)

---

## Verify the Application

1. Open the frontend in your browser:

   ```
   http://localhost:3000
   ```

2. Enter an email address and click **Send Notification**

3. The application will:

   * Trigger a background task
   * Poll the backend
   * Display real-time task status

---

## API Endpoints

### Trigger a Task

```http
POST /notify/?email=test@example.com
```

---

### Check Task Status

```http
GET /task_status/{task_id}
```

---

### API Documentation (Swagger)

```
http://localhost:8000/docs
```

---

## View Logs

To view logs for all services:

```bash
docker compose logs -f
```

---

## Stop the Application

```bash
docker compose down
```

---

## Configuration

* Environment variables are defined in the `docker-compose.yml` file
* You can modify values such as:

  * Redis connection URL
  * Backend configuration
  * Ports

---

## Troubleshooting

* Ensure Docker is running before executing commands
* If ports are already in use, update port mappings in `docker-compose.yml`
* Rebuild containers if dependencies change:

```bash
docker compose up --build
```

---

## Notes

* This setup is intended for local development and testing
* For production deployment, refer to Terraform and CI/CD configurations in the repository

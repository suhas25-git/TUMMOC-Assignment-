User
 ↓
S3 Static Website (Frontend)
 ↓
Application Load Balancer
 ↓
ECS Cluster (Fargate)

   ├── Backend Service (FastAPI)
   ├── Worker Service (Celery)
   └── Redis (ElastiCache)

CloudWatch → Logs
ECR → Docker Images
GitHub Actions → CI/CD
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/6d369099-3e47-4625-aa0f-89769df3bc55" />

<img width="1917" height="972" alt="image" src="https://github.com/user-attachments/assets/50bed8c1-407a-4ec5-ae09-4940726b1abe" />
<img width="1919" height="967" alt="image" src="https://github.com/user-attachments/assets/1bd34c0a-9b61-4dbb-b3a3-c8668b7a0352" />
<img width="1660" height="682" alt="image" src="https://github.com/user-attachments/assets/fc3b4e10-85d4-4ee6-a9d1-2028424e5c6d" />

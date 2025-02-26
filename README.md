# Automated AWS Deployment with Docker & GitHub Actions

## Overview
This project automates the deployment of containerized services using Docker, GitHub Actions, and AWS. The CI/CD pipeline builds and pushes images to Amazon ECR, while services are deployed on AWS EC2 with infrastructure managed via the AWS console. The setup ensures efficient deployments and scalability.

## Project Structure
```
project/
├── .github/workflows/       # CI/CD configurations for AWS
│   ├── aws-bcknd-rds-ci-cd.yml  # CI/CD pipeline for Backend RDS
│   ├── aws-bcknd-redis-ci-cd.yml # CI/CD pipeline for Backend Redis
│   ├── aws-frontend-ci-cd.yml    # CI/CD pipeline for Frontend
│
├── backend_rds/             # Backend service for PostgreSQL
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   ├── core/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│
├── backend_redis/           # Backend service for Redis caching
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   ├── core/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│
├── frontend/                # Frontend deployment files
│   ├── templates/
│   ├── Dockerfile
│   ├── config.json
│   ├── nginx.conf
│   ├── .env
│
├── docker-compose.yml       # Docker Compose setup
└── README.md                # Project documentation
```

## Prerequisites
Ensure you have the following installed:
- [Docker](https://www.docker.com/get-started)
- AWS CLI
- Git
- Python (for backend services)

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/project.git
   cd project
   ```
2. Set up AWS credentials:
   ```sh
   aws configure
   ```
3. Set up Docker and build the containers:
   ```sh
   docker-compose build
   ```

## CI/CD Pipeline
This project includes GitHub Actions workflows to automate the deployment process:
- **Backend RDS CI/CD**: Builds, pushes, and deploys the RDS backend service.
- **Backend Redis CI/CD**: Builds, pushes, and deploys the Redis backend service.
- **Frontend CI/CD**: Builds, pushes, and deploys the frontend service.

## Deployment
### Local Deployment
To start the entire application locally:
```sh
docker-compose up -d
```
This will run all services (Frontend, Backend RDS, Backend Redis, PostgreSQL, Redis) in separate containers.

### AWS Deployment
1. Push the latest Docker images to Amazon ECR:
   ```sh
   docker tag backend_rds:latest <ECR_REPOSITORY>:latest
   docker push <ECR_REPOSITORY>:latest
   ```
2. SSH into the EC2 instance and update the containers:
   ```sh
   ssh -i ~/.ssh/ec2_private_key.pem ec2-user@<ELASTIC_IP>
   docker pull <ECR_REPOSITORY>:latest
   docker-compose up -d backend_rds
   ```
   Repeat the process for `backend_redis` and `frontend`.

## Architecture
- **Backend RDS**: Runs on AWS EC2, connects to PostgreSQL.
- **Backend Redis**: Runs on AWS EC2, connects to Redis for caching.
- **Frontend**: Served via Nginx and Docker on AWS EC2.
- **CI/CD**: Automated deployments via GitHub Actions.

## Services Overview
### Docker Compose Setup
The `docker-compose.yml` file orchestrates the services:
- **Frontend** (Nginx)
- **Backend RDS** (PostgreSQL API)
- **Backend Redis** (Redis caching API)
- **Database (PostgreSQL)**
- **Redis**

To check running containers:
```sh
docker ps
```

## Contributors
- **Vitaliy Prymak** - Project Maintainer

## License
This project is licensed under the MIT License.


# Dockerized Test Execution Environment

## Overview
A containerized test execution infrastructure using Docker and Kubernetes for scalable, consistent, and parallel test execution across multiple environments.

## Problem Statement
Test environments were inconsistent across developer machines, CI servers, and staging environments. This led to flaky tests, "works on my machine" issues, and wasted time debugging environment-specific problems.

## Solution
Containerized the entire test execution stack using Docker, orchestrated with Kubernetes for scalable parallel execution, and provisioned using Terraform on AWS.

## Tech Stack
| Technology | Purpose |
|-----------|---------|
| Docker | Container runtime |
| Kubernetes | Container orchestration |
| Terraform | Infrastructure as Code |
| AWS (EC2, ECS, ECR) | Cloud infrastructure |
| Jenkins | CI/CD orchestration |
| Selenium Grid | Distributed test execution |

## Architecture
```
Developer Push --> Jenkins Pipeline --> Build Docker Image
                                              |
                                    Push to ECR Registry
                                              |
                                    K8s Deployment (Pods)
                                              |
                              ┌───────────────┼───────────────┐
                              │               │               │
                        Chrome Pod      Firefox Pod     Edge Pod
                              │               │               │
                              └───────────────┼───────────────┘
                                              |
                                    Test Results & Reports
```

## Docker Configuration
```dockerfile
FROM selenium/standalone-chrome:latest

COPY test-suite/ /app/tests/
COPY config/ /app/config/

RUN pip install -r /app/tests/requirements.txt

ENTRYPOINT ["pytest", "/app/tests/"]
```

## Kubernetes Deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: test-runner
spec:
  replicas: 5
  selector:
    matchLabels:
      app: test-runner
```

## Key Results
- Consistent test execution across all environments
- 3x faster execution with parallel pods
- Zero environment-related flaky tests
- Auto-scaling based on test queue size

## How to Run
```bash
docker build -t test-runner .
docker-compose up --scale chrome=5
kubectl apply -f k8s/deployment.yaml
```

## Author
**Suranjith Kumar J** - Senior SDET-2 | AI-Powered QAOps Engineer  
[LinkedIn](https://linkedin.com/in/suranjith-kumar-jeppu) | [Portfolio](https://suranjithkumarj111-lgtm.github.io/Suranjith_Projects)

# Ledger API – DevSecOps Secure Deployment

## Project Overview

This project secures and deploys the Ledger API microservice using Docker, Kubernetes, and DevSecOps best practices. The original application contained intentionally insecure configurations, which were identified and remediated.

---

## Objectives

- Harden the Docker image
- Remove hardcoded secrets
- Secure Kubernetes deployment
- Implement RBAC and Network Policies
- Scan for vulnerabilities and secrets
- Document security improvements

---

## Technology Stack

- Python
- Docker
- Kubernetes (Kind)
- Trivy
- Checkov
- Gitleaks
- GitHub Actions

---

## Security Improvements

### Docker Security

- Updated base image to `python:3.12-slim`
- Updated vulnerable Python dependencies
- Runs as a non-root user
- Disabled pip cache
- Cleaned package manager cache
- Improved image build process

---

### Kubernetes Security

Implemented the following Kubernetes security controls:

- Dedicated namespace (`payments`)
- Kubernetes Secret for sensitive values
- ServiceAccount
- RBAC (Role & RoleBinding)
- NetworkPolicy
- Security Context
- Least privilege deployment

---

## Security Scanning

### Trivy

Container images were scanned using Trivy.

Reports included:

- reports/starter-image-report.txt
- reports/secure-image-report.txt
- reports/secure-v2-image-report.txt
- reports/secure-v3-image-report.txt

---

### Checkov

Infrastructure-as-Code manifests were scanned using Checkov to identify Kubernetes security issues.

---

### Gitleaks

Repository scanned for hardcoded secrets.

Hardcoded secrets were removed from Kubernetes manifests and replaced with Kubernetes Secrets.

---

## Project Structure

```
.
├── app/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
│
├── deploy/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── namespace.yaml
│   ├── secret.yaml
│   ├── networkpolicy.yaml
│   └── serviceaccount.yaml
│
├── reports/
│   ├── starter-image-report.txt
│   ├── secure-image-report.txt
│   ├── secure-v2-image-report.txt
│   └── secure-v3-image-report.txt
│
└── README.md
```

---

## Build Docker Image

```bash
cd app

docker build -t ledger-api:secure-v3 .
```

---

## Load Image into Kind

```bash
kind load docker-image ledger-api:secure-v3 --name dodo-devsecops
```

---

## Deploy to Kubernetes

```bash
kubectl apply -f deploy/namespace.yaml
kubectl apply -f deploy/secret.yaml
kubectl apply -f deploy/serviceaccount.yaml
kubectl apply -f deploy/networkpolicy.yaml
kubectl apply -f deploy/deployment.yaml
kubectl apply -f deploy/service.yaml
```

---

## Verify Deployment

```bash
kubectl get pods -n payments

kubectl get svc -n payments

kubectl get networkpolicy -n payments

kubectl get role -n payments

kubectl get rolebinding -n payments
```

---

## Security Summary

This project demonstrates:

- Docker image hardening
- Updated application dependencies
- Non-root container execution
- Kubernetes Secrets
- RBAC
- Network Policies
- Kubernetes ServiceAccount
- Container vulnerability scanning
- Infrastructure-as-Code scanning
- Secret detection

---

## Future Improvements

- Add Admission Controller policies
- Integrate image signing (Cosign)
- Enforce Pod Security Standards
- Continuous vulnerability scanning in CI/CD
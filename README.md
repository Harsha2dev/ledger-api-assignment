# Dodo Payments – DevSecOps Security Assignment

## Overview

This repository contains my solution for the **Dodo Payments DevSecOps Security Engineer Technical Assignment**.

The project secures and deploys the vulnerable **ledger-api** application by implementing DevSecOps best practices across container security, Kubernetes hardening, GitOps, Zero Trust networking, supply chain security, and application security testing.

---

# Tasks Completed

## Task 1 – Secure Deployment

Implemented the following security controls:

- Hardened Docker image
- Updated Python dependencies
- Non-root container execution
- Read-only root filesystem
- Dropped Linux capabilities
- RuntimeDefault Seccomp profile
- Kubernetes Namespace
- ConfigMap
- Kubernetes Secret
- ServiceAccount
- RBAC (Role & RoleBinding)
- Resource Requests & Limits
- Liveness & Readiness Probes
- NetworkPolicy
- Kubernetes Ingress
- Reporting neighbour service deployment

---

## Task 2 – Secure CI/CD & Supply Chain

Implemented:

- GitHub Actions CI pipeline
- Trivy vulnerability scanning
- Gitleaks secret scanning
- Checkov Infrastructure-as-Code scanning
- SPDX SBOM generation
- Cosign image signing
- ArgoCD GitOps deployment
- Automated Synchronization
- Self-Healing
- Drift Detection

---

## Task 3 – Zero Trust Networking (Istio)

Implemented:

- Istio Service Mesh
- STRICT Mutual TLS (mTLS)
- AuthorizationPolicy
- Kubernetes NetworkPolicy
- Secure service-to-service communication

---

## Task 4 – Security Testing

Performed:

- Reconnaissance
- OWASP ZAP Security Scan
- SSRF Assessment
- YAML Deserialization Review
- HTTP Security Header Review

---

# Security Tools Used

- Docker
- Kubernetes (Kind)
- GitHub Actions
- Trivy
- Checkov
- Gitleaks
- Cosign
- ArgoCD
- Kyverno
- Istio
- OWASP ZAP

---

# Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── build.yml
│
├── app/
│   ├── app.py
│   ├── Dockerfile
│   └── requirements.txt
│
├── deploy/
│   ├── authorization-policy.yaml
│   ├── configmap.yaml
│   ├── deployment.yaml
│   ├── ingress.yaml
│   ├── kyverno-policy.yaml
│   ├── namespace.yaml
│   ├── neighbour.yaml
│   ├── network-policy.yaml
│   ├── peer-authentication.yaml
│   ├── secret.yaml
│   ├── service.yaml
│   └── serviceaccount.yaml
│
├── reports/
│   ├── pentest-report.md
│   ├── zap-report.pdf
│   ├── sbom.spdx.json
│   ├── starter-image-report.txt
│   ├── secure-image-report.txt
│   ├── secure-v2-image-report.txt
│   └── secure-v3-image-report.txt
│
├── screenshots/
│   ├── argocd-sync.png
│   ├── github-actions.png
│   ├── istio-mtls.png
│   ├── trivy-report.png
│   └── zap-scan.png
│
├── tests/
│   ├── kyverno-test-pod.yaml
│   └── kyverno-secure-test-pod.yaml
│
├── cosign.pub
└── README.md
```

---

# Reports

The **reports/** directory contains:

- Trivy vulnerability scan reports
- SPDX Software Bill of Materials (SBOM)
- OWASP ZAP Scan Report (PDF)
- Penetration Testing Report

---

# Screenshots

The **screenshots/** directory contains evidence of the completed implementation:

- ArgoCD GitOps Deployment
- GitHub Actions Pipeline
- Trivy Vulnerability Scan
- Istio mTLS Configuration
- OWASP ZAP Scan

---

# Deployment

Deploy all Kubernetes resources:

```bash
kubectl apply -f deploy/
```

---

# Verification

Verify the deployment using:

```bash
kubectl get pods -n payments
kubectl get deployments -n payments
kubectl get svc -n payments
kubectl get ingress -n payments
kubectl get networkpolicy -n payments
kubectl get peerauthentication -n payments
kubectl get authorizationpolicy -n payments
kubectl get application -n argocd
```

---

# Security Improvements

The project implements multiple layers of security, including:

- Secure Docker image hardening
- Non-root containers
- Kubernetes Secrets
- RBAC
- Service Accounts
- Network Policies
- Istio Service Mesh
- STRICT Mutual TLS
- Authorization Policies
- Kyverno Admission Policies
- GitOps deployment using ArgoCD
- Vulnerability scanning with Trivy
- Infrastructure scanning with Checkov
- Secret scanning with Gitleaks
- Software Bill of Materials (SBOM)
- Image signing using Cosign
- Application security testing using OWASP ZAP

---

# Final Outcome

This project demonstrates a complete DevSecOps workflow by combining secure containerization, Kubernetes hardening, GitOps deployment, Zero Trust networking, admission control, supply chain security, and application security testing.

The solution satisfies the assignment requirements while following modern cloud-native security best practices.

---

## Author

**Harsha MN**

DevSecOps Security Engineer Assignment – Dodo Payments
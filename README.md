# Dodo Payments – DevSecOps Security Assignment

## Overview

This repository contains my solution for the Dodo Payments DevSecOps Security Engineer assignment.

The project hardens and secures the vulnerable `ledger-api` application using modern DevSecOps practices, including container security, Kubernetes hardening, GitOps, service mesh security, admission control, supply-chain security, and security testing.

---

# Tasks Completed

## Task 1 – Secure Deployment

Implemented:

- Hardened Docker image
- Python dependency updates
- Non-root container execution
- Read-only root filesystem
- Dropped Linux capabilities
- RuntimeDefault seccomp profile
- Kubernetes Namespace
- ConfigMap
- Secret
- ServiceAccount
- RBAC (Role & RoleBinding)
- Resource requests & limits
- Liveness & Readiness probes
- NetworkPolicy
- Ingress
- Reporting neighbour service

---

## Task 2 – Secure CI/CD & Supply Chain

Implemented:

- GitHub Actions CI pipeline
- Trivy vulnerability scanning
- Gitleaks secret scanning
- Checkov IaC scanning
- SPDX SBOM generation
- Cosign image signing
- ArgoCD GitOps deployment
- Auto Sync
- Self Healing
- Drift Detection

---

## Task 3 – Zero Trust Networking (Istio)

Implemented:

- Istio Service Mesh
- STRICT mTLS
- AuthorizationPolicy
- Kubernetes NetworkPolicy
- Secure service-to-service communication

---

## Task 4 – Security Testing

Performed:

- OWASP ZAP scan
- SSRF assessment
- YAML deserialization review
- HTTP security header analysis
- Basic reconnaissance

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
├── app/
├── deploy/
├── reports/
├── tests/
├── .github/workflows/
└── README.md
```

---

# Reports

Located under `reports/`

- Trivy scan reports
- SPDX SBOM

---

# Test Manifests

Located under `tests/`

- Kyverno insecure pod
- Kyverno secure pod

---

# Deployment

```bash
kubectl apply -f deploy/
```

---

# Verification

```bash
kubectl get pods -n payments
kubectl get deployments -n payments
kubectl get networkpolicy -n payments
kubectl get peerauthentication -n payments
kubectl get authorizationpolicy -n payments
```

---

# Notes

- The application is managed through ArgoCD using GitOps.
- Kyverno enforces pod security policies.
- Istio provides mutual TLS and authorization controls.
- Supply-chain security includes SBOM generation and Cosign signing.
- Security validation was performed using Trivy, Checkov, Gitleaks, and OWASP ZAP.
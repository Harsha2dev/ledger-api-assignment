# Dodo Payments – DevSecOps Security Assessment

## Overview

This repository contains my solution for the Dodo Payments DevSecOps Security Engineer technical assessment.

The project secures the vulnerable `ledger-api` microservice by implementing workload hardening, supply-chain security, GitOps, service mesh security, and penetration testing.

---

# Task 1 – Deploy & Harden

## Implemented

- Hardened Docker image
- Non-root container
- Read-only root filesystem
- Dropped Linux capabilities
- RuntimeDefault seccomp profile
- Resource requests and limits
- Liveness & readiness probes
- Kubernetes Secret
- ConfigMap
- ServiceAccount
- RBAC
- NetworkPolicy
- Kyverno admission policies
- Reporting neighbour service

---

# Task 2 – Secure CI/CD & Supply Chain

Implemented

- GitHub Actions pipeline
- Trivy image scanning
- Gitleaks secret scanning
- Checkov Kubernetes scanning
- SBOM generation (SPDX)
- Cosign image signing
- ArgoCD GitOps
- Drift detection
- Self-healing deployment

---

# Task 3 – Zero Trust (Istio)

Implemented

- Istio service mesh
- STRICT mTLS
- AuthorizationPolicy
- NetworkPolicy
- Service-to-service authorization

---

# Task 4 – Security Testing

Recon

- Technology fingerprinting
- Attack surface review

Penetration Testing

- OWASP ZAP
- SSRF assessment
- YAML deserialization review

---

# Security Tools

- Trivy
- Checkov
- Gitleaks
- Cosign
- Kyverno
- ArgoCD
- Istio
- OWASP ZAP

---

# Repository Structure

(app, deploy, reports, tests, etc.)

---

# Screenshots

- ArgoCD Sync
- Kyverno policy enforcement
- Istio mTLS
- Trivy results
- ZAP scan
- GitHub Actions

---

# Results

Summarize the security improvements and mention any environment-specific observations (for example, local Ingress health depending on the presence of an Ingress controller).

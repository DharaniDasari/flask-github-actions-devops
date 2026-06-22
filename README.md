# flask-github-actions-devops

# 🚀 Automated CI/CD DevOps Pipeline (Dockerized Flask App)

A production-grade Python Flask microservice integrated with a comprehensive, multi-stage **GitHub Actions CI/CD pipeline**. This repository serves as a blueprint for automated testing, containerization layers with optimized Docker layer caching, and continuous deployment tracking to Render Cloud.

---

## 🌟 Strategic Key Highlights
* **Automated CI Blueprint:** Implements a fully automated GitHub Actions workflow triggered instantly on `push` and `pull_request` triggers to the `main` branch.
* **Optimized Docker Cache Layers:** Features a fine-tuned `Dockerfile` that copies requirements separately, leveraging Docker layer caching to reduce container image compilation speeds from minutes to seconds.
* **Continuous Delivery Architecture:** Securely authenticates against Docker Hub via encrypted repo secrets, building and pushing labeled `:latest` images seamlessly.
* **Automated CD Trigger:** Integrates post-build webhooks to automatically signal Render for zero-downtime microservice deployments immediately following successful pipeline executions.

---

## 🧩 System Lifecycle Flow

```text
Local Dev ──> Git Push (main) ──> GitHub Actions Runner
                                       │
      ┌────────────────────────────────┴────────────────────────┐
      ▼ (Job 1: Test)                                           ▼ (Job 2: Publish & Deploy)
[ build-and-test ]                                       [ build-and-publish ]
├── Env Setup (Python 3.10)                              ├── Docker Buildx Setup
├── Install Dependencies                                 ├── Docker Hub Login (Secrets)
└── Execute Test Suite (Pytest)                          ├── Push Image (flask-app:latest)
                                                         └── Webhook Hit ──> [ Render Cloud ]

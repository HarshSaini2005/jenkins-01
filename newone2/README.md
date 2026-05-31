# CI/CD Pipeline with Jenkins

This repository contains a Jenkins pipeline configuration that automates the build, test, and verification process for a full-stack application with:

- **Backend**: Java 11 + Maven 3.8.1
- **Frontend**: Node.js 16 (Alpine)
- **Database**: MySQL 8 (latest)

## 📋 Table of Contents

- [Pipeline Overview](#pipeline-overview)
- [Prerequisites](#prerequisites)
- [Pipeline Stages](#pipeline-stages)
- [Setup Instructions](#setup-instructions)
- [Customization](#customization)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## 🚀 Pipeline Overview

The Jenkins pipeline (`Jenkinsfile`) runs three main stages using Docker containers:

1. **Backend Build** - Compiles Java/Maven project
2. **Frontend Build** - Installs dependencies and builds Node.js project
3. **Database Test** - Spins up MySQL and executes `SELECT * FROM xyz`

Each stage runs in an isolated Docker container, ensuring consistency across different environments.

## 📦 Prerequisites

### Required Software
- **Jenkins** 2.319.3 or higher
- **Docker** 20.10.0 or higher
- **Jenkins Plugins**:
  - Docker Pipeline
  - Pipeline Plugin
  - Git Plugin

### Jenkins Configuration
1. Ensure Docker is installed on your Jenkins agent/node
2. Jenkins user must have permission to run Docker commands
3. Configure Docker cloud in Jenkins (if using dynamic agents)

## 🔧 Pipeline Stages

### Stage 1: Backend Build
```yaml
Docker Image: maven:3.8.1-adoptopenjdk-11
Commands:
  - mvn clean compile
  - mvn test (optional)

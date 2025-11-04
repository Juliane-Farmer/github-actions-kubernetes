# GitHub Actions Kubernetes Demo

This repository demonstrates a CI/CD pipeline using GitHub Actions to deploy a Python Flask application to Kubernetes using Helm.

## Project Structure

```
├─ app/                    # Python Flask application
│  ├─ main.py             # Main application file
│  └─ requirements.txt    # Python dependencies
├─ k8s/                   # Kubernetes manifests
│  ├─ pod-template.yaml   # Pod definition
│  ├─ deployment.yaml     # Deployment configuration
│  └─ service.yaml        # Service configuration
├─ helm/                  # Helm chart
│  └─ hello-chart/       
│     ├─ Chart.yaml      # Chart metadata
│     ├─ values.yaml     # Default values
│     └─ templates/      # Helm templates
│        ├─ deployment.yaml
│        └─ service.yaml
├─ .github/
│  └─ workflows/
│     └─ ci-deploy.yaml  # GitHub Actions workflow
├─ Dockerfile            # Container image definition
└─ README.md            # This file
```

## Prerequisites

- Docker
- Kubernetes cluster
- Helm
- GitHub account
- Docker Hub account

## Setup

1. Fork this repository
2. Add the following secrets to your GitHub repository:
   - `DOCKER_USERNAME`: Your Docker Hub username
   - `DOCKER_PASSWORD`: Your Docker Hub password
   - `KUBE_CONFIG`: Your Kubernetes cluster configuration

## Local Development

1. Install dependencies:
   ```bash
   cd app
   pip install -r requirements.txt
   ```

2. Run the application:
   ```bash
   python main.py
   ```

## Deployment

The application is automatically deployed when changes are pushed to the main branch. The pipeline:

1. Builds the Docker image
2. Pushes it to Docker Hub
3. Deploys to Kubernetes using Helm

To deploy manually:

```bash
helm upgrade --install hello-app ./helm/hello-chart
```

## License

MIT
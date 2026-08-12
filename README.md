# CI/CD Demo App

A simple Node.js/Express app deployed through a fully automated CI/CD pipeline.

## Architecture
## Tech Stack

- **AWS EC2** — compute
- **Terraform** — infrastructure as code
- **Jenkins** — CI/CD orchestration
- **Docker** — containerization
- **Nginx** — reverse proxy
- **GitHub Webhooks** — automatic build triggers
- **Node.js / Express** — application
- **Jest** — testing

## How it works

1. Code is pushed to this repository
2. A GitHub webhook notifies Jenkins
3. Jenkins pulls the latest code, installs dependencies, and runs tests
4. On success, Jenkins builds a new Docker image
5. The old container is stopped and replaced with the new one
6. Nginx reverse-proxies incoming traffic on port 80 to the container on port 3000

## Infrastructure

All AWS infrastructure (EC2 instance, security group, key pair) is provisioned via Terraform — see the companion [cicd-infra](../cicd-infra) repository/folder.

## Local development

```bash
npm install
npm test
node app.js
```

Visit `http://localhost:3000`.

## CI/CD Pipeline

See [`Jenkinsfile`](./Jenkinsfile) for the full pipeline definition: checkout → install & test → build Docker image → deploy.

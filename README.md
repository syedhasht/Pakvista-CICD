# PakVista CI/CD

PakVista is a static tourism website about Pakistan's major travel destinations. This project demonstrates a complete multi-environment CI/CD pipeline using GitHub Actions, Docker Hub, and Render.

## Project Overview

This project is built for the DevOps Fundamentals term project. It follows a professional delivery workflow across three isolated environments:

- Development
- Staging
- Production

Each environment has a separate CI workflow and a separate CD workflow. The website is containerized using Docker and deployed to Render through automated GitHub Actions pipelines.

## Live URLs

| Environment | URL |
|---|---|
| Development | https://pakvista-dev.onrender.com |
| Staging | https://pakvista-staging.onrender.com |
| Production | https://pakvista-prod.onrender.com |

## Repository

GitHub Repository:

https://github.com/syedhasht/Pakvista-CICD

## Team Members

| Name | GitHub Username | Role | Assigned Page | Assigned Workflow |
|---|---|---|---|---|
| Syed Hashim | syedhasht | Team Lead | index.html | ci-dev.yml, cd-prod.yml |
| Bakhtawar | Bakhtawarrahat33 | Member | lahore.html | cd-dev.yml |
| Ayman | AymanSheikh6 | Member | hunza.html | ci-staging.yml |
| Muhammad Zain Farrukh | mzain6 | Member | karachi.html, swat.html | cd-staging.yml, ci-prod.yml |

## Website Pages

| Page | Description |
|---|---|
| index.html | Home page introducing PakVista and Pakistan tourism |
| lahore.html | Lahore tourism page covering Badshahi Mosque, Lahore Fort, and Shalimar Gardens |
| hunza.html | Hunza Valley page covering Rakaposhi Viewpoint, Attabad Lake, and Baltit Fort |
| karachi.html | Karachi page covering Clifton Beach, Mohatta Palace, and Pakistan Maritime Museum |
| swat.html | Swat Valley page covering Malam Jabba, Mingora Bazaar, and Swat Museum |

## Technology Stack

- HTML5
- CSS3
- Docker
- Nginx Alpine
- GitHub Actions
- Docker Hub
- Render
- Parcel
- HTMLHint
- Stylelint

## Repository Structure

Pakvista-CICD/
├── index.html
├── lahore.html
├── hunza.html
├── karachi.html
├── swat.html
├── style.css
├── Dockerfile
├── package.json
├── .htmlhintrc
├── .stylelintrc.json
├── TermProject_Spring2026.docx
└── .github/
    └── workflows/
        ├── ci-dev.yml
        ├── cd-dev.yml
        ├── ci-staging.yml
        ├── cd-staging.yml
        ├── ci-prod.yml
        └── cd-prod.yml

## Branching Strategy

The project follows this GitFlow-style branching model:

feature branch -> develop -> staging -> main

| Branch | Purpose |
|---|---|
| feature/* | Individual member work |
| develop | Development integration branch |
| staging | Pre-production testing branch |
| main | Production branch |

## CI/CD Pipeline

### Development

| Workflow | Trigger | Purpose |
|---|---|---|
| ci-dev.yml | Pull request to develop | Lint, build, Docker build, Docker push |
| cd-dev.yml | Push to develop | Trigger Render development deployment |

### Staging

| Workflow | Trigger | Purpose |
|---|---|---|
| ci-staging.yml | Pull request to staging | Lint, build, Docker build, Docker push |
| cd-staging.yml | Push to staging | Trigger Render staging deployment |

### Production

| Workflow | Trigger | Purpose |
|---|---|---|
| ci-prod.yml | Pull request to main | Lint, build, Docker build, Docker push |
| cd-prod.yml | Push to main | Trigger Render production deployment |

## Docker Image Tags

| Environment | Docker Tags |
|---|---|
| Development | dev-latest, dev-sha |
| Staging | staging-latest, staging-sha |
| Production | prod-latest, prod-sha |

Docker Hub repository:

syedhasht/pakvista-cicd

## Dockerfile

The project uses an Nginx Alpine image to serve static HTML and CSS files.

FROM nginx:alpine
COPY *.html /usr/share/nginx/html/
COPY style.css /usr/share/nginx/html/
EXPOSE 80

## Local Setup

Clone the repository:

git clone https://github.com/syedhasht/Pakvista-CICD.git
cd Pakvista-CICD

Install dependencies:

npm install

Run HTML lint:

npm run lint:html

Run CSS lint:

npm run lint:css

Build the static site:

npm run build

## Docker Local Run

Build Docker image locally:

docker build -t pakvista-cicd .

Run container:

docker run -p 8080:80 pakvista-cicd

Open in browser:

http://localhost:8080

## Member Workflow

Each member works on their own feature branch.

Example:

git checkout develop
git pull origin develop
git checkout -b feature/username/page-name

After completing work:

git add .
git commit -m "Add assigned page and workflow"
git push origin feature/username/page-name

Then open a pull request to develop.

## Deployment Flow

Feature Branch
    ↓
Pull Request to develop
    ↓
ci-dev passes
    ↓
Merge into develop
    ↓
cd-dev deploys to Render development
    ↓
Pull Request: develop to staging
    ↓
ci-staging passes
    ↓
Merge into staging
    ↓
cd-staging deploys to Render staging
    ↓
Pull Request: staging to main
    ↓
ci-prod passes
    ↓
Merge into main
    ↓
cd-prod deploys to Render production

## GitHub Secrets

### Repository Secrets

| Secret | Purpose |
|---|---|
| DOCKERHUB_USERNAME | Docker Hub username |
| DOCKERHUB_TOKEN | Docker Hub access token |

### Environment Secrets

| Environment | Secret |
|---|---|
| development | RENDER_DEPLOY_HOOK_DEV_URL |
| staging | RENDER_DEPLOY_HOOK_STAGING_URL |
| production | RENDER_DEPLOY_HOOK_PROD_URL |

## Screenshots Required for Submission

The final submission document should include screenshots of:

1. GitHub environments and secrets
2. CI workflow runs for member pull requests
3. Docker Hub image tags
4. CD workflow runs for development, staging, and production
5. Live Render development service
6. Live Render staging service
7. Live Render production service
8. Term project document visible in the repository
9. Branch protection or rulesets

## Project Rules

- No JavaScript is used.
- All pages are built using HTML5 and CSS3 only.
- All pages use the shared style.css.
- All deployments are triggered through GitHub Actions.
- Docker images are pushed to Docker Hub.
- Render deployments are triggered through deploy hooks.
- Members must work through feature branches and pull requests.

## Status

| Item | Status |
|---|---|
| Repository setup | Completed |
| Development CI | Completed |
| Development deployment | Completed |
| Docker Hub dev image | Completed |
| Staging setup | Completed |
| Production setup | Completed |
| Member PRs | Completed |

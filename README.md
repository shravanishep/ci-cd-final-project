# CI/CD Final Project

## Project Name: ci-cd-final-project

This repository contains the CI/CD pipeline and microservice application for the Coursera course **CI/CD Tools and Practices Final Project**.

### Project Details
- **Project Name**: ci-cd-final-project
- **Course**: CI/CD Tools and Practices
- **Application**: Hit Counter RESTful Microservice
- **Runtime**: Python 3.9 / Flask
- **CI Tool**: GitHub Actions (`.github/workflows/workflow.yml`)
- **CD Tool**: OpenShift / Tekton Pipelines (`.tekton/tasks.yml`)
- **Default Port**: 8000

## Quick Start

### Setup Environment
```bash
bash bin/setup.sh
```

### Run Tests and Linting
```bash
flake8 service tests --count --select=E9,F63,F7,F82 --show-source --statistics
flake8 . --count --max-complexity=10 --max-line-length=127 --statistics
nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
```

### Run Locally
```bash
gunicorn --bind 0.0.0.0:8000 service:app
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Root service information |
| GET | `/health` | Health check endpoint |
| GET | `/counters` | List all counters |
| POST | `/counters/<name>` | Create a new counter |
| PUT | `/counters/<name>` | Increment counter value |
| GET | `/counters/<name>` | Read counter value |
| DELETE | `/counters/<name>` | Delete counter |

## CI/CD Pipeline
- **GitHub Actions Workflow**: Linting with `flake8` and unit testing with `nosetests`
- **Tekton Pipeline Tasks**: `cleanup`, `git-clone`, `flake8`, `nose`, `buildah`, `deploy`

## License
Licensed under the Apache License. See [LICENSE](/LICENSE)

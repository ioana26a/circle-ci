# Project-CircleCI

This project demonstrates **CI/CD automation with CircleCI** for a Dockerized web application stack.

## CI/CD Highlights

- **Automated Testing & Linting:** Every commit triggers `pytest` and `flake8` to ensure code quality.
- **Docker Build & Push:** CircleCI builds Docker images and pushes them to AWS ECR.
- **Automated Deployment:** The pipeline deploys the latest image to AWS EC2 via SSH.
- **Orchestration:** Uses Docker Compose for local development and production parity.

See the [`.circleci/config.yml`](.circleci/config.yml) for the complete pipeline configuration.

## Stack Overview

- **Flask** backend API (Python)
- **MariaDB** database
- **NGINX** web server
- **Docker Compose** for orchestration

## Key Pipeline Steps

1. **Test & Lint:**
   Runs `pytest` and `flake8` on every commit.
2. **Build & Push:**
   Builds Docker image and pushes to AWS ECR.
3. **Deploy:**
   SSHes into EC2 and deploys the latest image.

## Local Development

```sh
cd app
docker compose up --build
```

## Project Structure

```
├── app/
│   ├── app.py
│   ├── init_db.py
│   ├── requirements.txt
│   ├── Dockerfile
│   ├── docker-compose.yml
│   ├── default.conf
│   ├── index.html
│   └── test_app.py
└── .circleci/
    └── config.yml
```

## API Endpoints

- `GET /` — Environment info
- `GET /api/data` — Up to 10 user records
- `GET /api/data/<limit>` — Up to `<limit>` user records (max 1000)
- `GET /api/health` — Health and DB status


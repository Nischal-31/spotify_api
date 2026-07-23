# 🎵 Spotify API - DevOps Deployment with FastAPI, Docker & AWS

A production-ready Spotify-inspired REST API built with **FastAPI**, **PostgreSQL**, **Docker**, **Nginx**, **GitHub Actions**, and **AWS EC2**.

This project demonstrates a complete DevOps workflow including containerization, CI/CD, reverse proxy configuration, and cloud deployment.

---

# 🚀 Tech Stack

- FastAPI
- PostgreSQL
- SQLAlchemy
- Docker & Docker Compose
- Nginx
- AWS EC2
- GitHub Actions
- Docker Hub
- JWT Authentication

---

# 📁 Project Structure

```
spotify-api/
│
├── .github/
│   └── workflows/
│       └── deploy.yml
│
├── app/
│   ├── api/
│   ├── core/
│   ├── database.py
│   ├── main.py
│   ├── models/
│   ├── schemas/
│   └── static/
│
├── nginx/
│   └── nginx.conf
│
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env.example
└── README.md
```

---

# ✨ Features

- User Registration
- User Login
- JWT Authentication
- Password Hashing (bcrypt)
- PostgreSQL Database
- Dockerized Application
- Nginx Reverse Proxy
- CI/CD using GitHub Actions
- Automatic Docker Hub Deployment
- Automatic EC2 Deployment

---

# 🏗 Architecture

```
                Git Push
                   │
                   ▼
          GitHub Repository
                   │
                   ▼
          GitHub Actions CI/CD
                   │
       Build Docker Image
                   │
                   ▼
             Docker Hub
                   │
                   ▼
             AWS EC2 Server
                   │
        docker compose pull
                   │
                   ▼
      Nginx → FastAPI → PostgreSQL
```

---

# ⚙️ Local Development

## Clone Repository

```bash
git clone https://github.com/Nischal-31/spotify-api.git

cd spotify-api
```

---

## Create Environment File

Create a `.env` file.

Example:

```env
APP_NAME=Spotify API

SECRET_KEY=your_secret_key

ALGORITHM=HS256

ACCESS_TOKEN_EXPIRE_MINUTES=60

DATABASE_URL=postgresql://postgres:password@db:5432/spotify_db

POSTGRES_DB=spotify_db

POSTGRES_USER=postgres

POSTGRES_PASSWORD=password
```

---

## Run using Docker

```bash
docker compose up --build
```

API:

```
http://localhost/docs
```

Swagger UI will be available automatically.

---

# 🐳 Docker

## Build Image

```bash
docker build -t spotify-api .
```

## Run

```bash
docker run -p 8000:8000 spotify-api
```

---

# Docker Compose

```bash
docker compose up -d
```

Services:

- FastAPI
- PostgreSQL
- Nginx

---

# ☁ AWS EC2 Deployment

Launch an Ubuntu EC2 instance.

Install:

- Docker
- Docker Compose
- Git

Clone the repository.

Create the `.env` file.

Start containers.

```bash
docker compose up -d
```

---

# 🔄 CI/CD Pipeline

Every push to the `master` branch automatically:

1. Builds Docker image
2. Pushes image to Docker Hub
3. SSH into EC2
4. Pulls latest image
5. Restarts containers

Workflow file:

```
.github/workflows/deploy.yml
```

---

# 🔐 GitHub Secrets

Configure the following repository secrets.

| Secret | Description |
|---------|-------------|
| DOCKERHUB_USERNAME | Docker Hub Username |
| DOCKERHUB_TOKEN | Docker Hub Access Token |
| EC2_HOST | Public EC2 IP |
| EC2_USER | EC2 Username |
| EC2_SSH_KEY | Private SSH Key |

---

# 📦 Docker Images

The deployment uses Docker Hub images.

Example:

```
username/spotify-api:latest
```

---

# 🌐 Reverse Proxy

Nginx listens on:

```
Port 80
```

and forwards requests to

```
FastAPI (Port 8000)
```

---

# 🗄 Database

PostgreSQL runs inside Docker.

Useful commands:

Connect

```bash
docker compose exec db psql -U postgres -d spotify_db
```

Show Tables

```sql
\dt
```

Show Users

```sql
SELECT * FROM users;
```

Exit

```sql
\q
```

---

# 📋 Useful Docker Commands

View containers

```bash
docker compose ps
```

Logs

```bash
docker compose logs web

docker compose logs db

docker compose logs nginx
```

Restart

```bash
docker compose restart web
```

Stop

```bash
docker compose down
```

Rebuild

```bash
docker compose up --build
```

---

# 📌 API Documentation

After deployment:

```
http://YOUR_SERVER_IP/docs
```

Example Request

```json
{
  "email": "user@example.com",
  "password": "Password123",
  "role": "admin",
  "is_active": true
}
```

---

# 🔑 Authentication

Passwords are securely hashed using bcrypt before being stored in PostgreSQL.

Authentication uses JWT access tokens.

Protected endpoints require:

```
Authorization: Bearer <token>
```

---

# 🛠 Troubleshooting

Check running containers

```bash
docker compose ps
```

View logs

```bash
docker compose logs -f web

docker compose logs -f db

docker compose logs -f nginx
```

Test locally

```bash
curl http://127.0.0.1

curl http://127.0.0.1/docs
```

---

# 📚 Future Improvements

- Refresh Tokens
- Spotify OAuth
- Redis Caching
- Prometheus Monitoring
- Grafana Dashboard
- Kubernetes Deployment
- HTTPS using Let's Encrypt
- Terraform Infrastructure

---

# 👨‍💻 Author

**Nischal Moktan**

GitHub

https://github.com/Nischal-31

Docker Hub

https://hub.docker.com/u/nischaldev31

---

## ⭐ If you found this project helpful, consider giving it a star!

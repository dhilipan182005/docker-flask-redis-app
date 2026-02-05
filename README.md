# Docker Flask + Redis Application

This repository demonstrates a **multi-container Docker application** consisting of:

* A **Flask web application (Python)**
* A **Redis database (cache)**
* A custom Docker network
* Environment variables for service discovery
* Docker volumes for data persistence

This project is commonly used as a Docker learning lab or DevOps assignment.

---

## 🚀 Features

* Containerized Flask web app
* Redis as an external data store
* Inter-container communication using Docker networking
* Environment variable configuration
* Persistent Redis storage using Docker volumes
* Exposed web service on port **5000**

---

## 🛠️ Project Structure

```
docker-flask-redis-app/
│
├── app.py
├── requirements.txt
└── Dockerfile
```

---

## 📦 Prerequisites

Make sure you have installed:

* Docker Desktop (Windows/Mac) or Docker Engine (Linux)
* VS Code (recommended)

---

## 🏗️ Build the Docker Image

```bash
docker build -t flask-redis-app:1.0 .
```

---

## 🌐 Create a Docker Network

```bash
docker network create web-network
```

---

## 🗄️ Run Redis Container

```bash
docker run -d --name redis-server --network web-network redis
```

---

## 🖥️ Run Flask Application

```bash
docker run -d --name web-app \
  --network web-network \
  -e REDIS_HOST=redis-server \
  -p 5000:5000 \
  flask-redis-app:1.0
```

---

## 🌍 Access the Application

Open your browser and go to:

```
http://localhost:5000
```

Refresh the page multiple times — the visitor counter should increase.

---

## 💾 Enable Redis Persistence (Optional but Recommended)

Create a volume:

```bash
docker volume create redis-data
```

Restart Redis with volume:

```bash
docker rm -f redis-server
docker run -d --name redis-server \
  --network web-network \
  -v redis-data:/data redis
```

---

## 🐞 Useful Docker Debug Commands

```bash
docker ps
docker logs web-app
docker logs -f web-app
docker inspect web-app
docker network inspect web-network
docker volume ls
```

---

## 📚 What You Learned (Learning Outcomes)

By completing this project, you have practiced:

* Writing a Dockerfile
* Building a custom Docker image
* Running multi-container applications
* Using Docker networking
* Passing environment variables to containers
* Persisting data with Docker volumes
* Debugging containers using logs and inspect commands

---

## 📜 License

This project is for educational purposes.

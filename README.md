# 🚀 VProfile – Containerized Multi-Tier Java Application

### Docker & Docker Compose | DevOps Practice Project

## 📌 Project Overview

VProfile is a **multi-tier monolithic Java web application** containerized using **Docker** and orchestrated with **Docker Compose**.
This project demonstrates how a **real-world enterprise** application can be deployed using multiple interconnected backend services in a production-like environment.

## ⚠️ Important Note (Transparency for Recruiters)

The **application source code and dependencies** are cloned from the **well-known VProfile project**, which is widely used for **DevOps hands-on practice**.

### 👉 My contribution focuses on:

● Containerization using Docker

● Multi-service orchestration with Docker Compose

● Environment & configuration management

● Service-to-service networking

● Deployment & troubleshooting


## 🏗️ Architecture Overview

```
+-------------------+
|    vproweb        |
|  Frontend (Web)   |
+---------+---------+
          |
          v
+-------------------+
|    vproapp        |
| Spring + Tomcat   |
| Backend Service   |
+----+-------+------+
     |       |
     v       v
+---------+  +-------------+  +-----------+
| vprodb  |  | vprocache   |  | vpromq    |
| MySQL   |  | Memcached   |  | RabbitMQ  |
+---------+  +-------------+  +-----------+
```

## 🧰 Tech Stack

●  **Backend:** Java, Spring MVC, Apache Tomcat

●  **Frontend:** JSP

●  **Database:** MySQL

●  **Caching:** Memcached

●  **Messaging:** RabbitMQ

●  **Containerization:** Docker

●  **Orchestration:** Docker Compose

## 📂 Project Structure

```
vprofile-project/
│
├── app/                 # Backend Dockerfile
├── web/                 # Frontend service  Dockerfile & nginconfigs
├── db/                  # Dockerfile, Database configs & .env
├── src/                 # Java source code
├── docker-compose.yml   # Multi-container orchestration
└── README.md
```

## ⚙️ Prerequisites

● Docker

● Docker Compose

● Git

● Minimum **4 GB RAM**

## 🚀 Setup & Deployment

1️⃣ **Clone the Repository**
```
https://github.com/Shikha-1811/vprofile-containerized-app.git
cd vprofile-containerized-app
```

2️⃣ **Start Services**

```
docker compose up -d
```

3️⃣ **Verify Containers**

```
docker ps
```

## 🔐 Configuration & Secrets Management
### 📄 Environment Variables

All sensitive credentials (**database, RabbitMQ, etc.**) are **securely stored** in:

```
db/.env
```

### ⚠️ Credentials are intentionally not hard-coded or exposed in this repository.
Refer to the ```.env``` file for required environment variables.

## ⚙️ Application Properties

#### Location:

```
src/main/resources/application.properties
```

Configured services include:

● MySQL database connection

● Memcached server

● RabbitMQ message broker

● Spring MVC & JSP view resolver

> All service hostnames align with Docker Compose service names.

## 🌐 Accessing the Application

**Frontend (vproweb):**	http://localhost/

**Backend (Tomcat):**	http://localhost:8080/

**RabbitMQ Management:**	http://localhost:15672/

> Login credentials are available inside db/.env.

## 🐳 Docker Build Details
### Backend Dockerfile

●  **Multi-stage Docker build**

● **Build Stage:**  ```maven:3.9.9-eclipse-temurin-21```

● **Runtime Stage:**  ```tomcat:9-jdk21-temurin```

● **WAR deployed to Tomcat**

● Port **8080** exposed

### Docker Compose Services

● **vprodb →** MySQL

● **vprocache →** Memcached

● **vpromq →** RabbitMQ

● **vproapp →** Spring + Tomcat backend

● **vproweb →** Frontend

## 🛠️ Logs & Troubleshooting
#### View Logs

```
docker compose logs -f vproapp
docker compose logs -f vprodb
```

## Common Issues

● MySQL container fails:
   → Verify ``` .env ``` configuration

● RabbitMQ connection issue:
→ Ensure service hostname matches ```application.properties```

## 🤝 Practice & Contribution

This project is **open for learning and hands-on practice.**

● Fork the repository

● Modify Docker Compose or services

● Add CI/CD, Kubernetes, monitoring, or cloud deployment

● Raise a Pull Request for improvements

> Contributions, enhancements, and DevOps experiments are always welcome.


## 🔗 Project Links

```
- 🔗 GitHub Repository: https://github.com/Shikha-1811/vprofile-containerized-app.git
- 🔗 LinkedIn Profile: https://linkedin.com/in/shikha-pal-095b9a27b
```

## 📸 Application Output Screenshots


### 📸 Application Preview

output_1.png
output_2.png
output_3.png



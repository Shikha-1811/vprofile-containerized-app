# 🚀 VProfile – Containerized Multi-Tier Application (Docker & Docker Compose)

## 📌 Project Overview

This project demonstrates the **containerization and deployment of a real-world multi-tier Java web application** using **Docker and Docker Compose**.  
The application follows a **production-like architecture** with separate services for frontend, backend, database, caching, and messaging.

The main objective of this project is to **practice DevOps concepts**, including containerization, service orchestration, inter-service communication, and environment-based configuration.

---



## 🏗 Architecture

                        ┌──────────────┐
                        │   Browser    │
                        │  (User UI)   │
                        └──────┬───────┘
                               │ HTTP (80)
                               ▼
                     ┌────────────────────┐
                     │     vproweb        │
                     │   Nginx Frontend   │
                     └────────┬──────────┘
                               │ HTTP (8080)
                               ▼
                     ┌────────────────────┐
                     │     vproapp        │
                     │ Spring MVC +       │
                     │ Apache Tomcat      │
                     └──────┬─────┬──────┘
                            │     │
            ┌───────────────┘     └───────────────┐
            ▼                                     ▼
┌────────────────────┐               ┌────────────────────┐
│      vprodb        │               │      vpromq        │
│     MySQL DB       │               │     RabbitMQ       │
│   Port: 3306       │               │    Port: 5672      │
└────────────────────┘               └────────────────────┘
            ▲
            │
┌────────────────────┐
│    vprocache       │
│    Memcached       │
│   Port: 11211      │
└────────────────────┘

## 🧰 Tech Stack

- Java (Spring MVC)
- Apache Tomcat
- MySQL
- Memcached
- RabbitMQ
- Docker
- Docker Compose
- Maven

---

## 📂 Project Structure

vprofile-project/
│
├── app/ # Application Dockerfile (multi-stage build)
├── db/ # MySQL Dockerfile and environment variables
├── web/ # Frontend service
├── src/ # Java source code
├── pom.xml # Maven build configuration
└── docker-compose.yaml # Multi-container orchestration



---

## ✅ Prerequisites

- Docker
- Docker Compose
- Git
- Minimum 4GB RAM recommended

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Shikha-1811/vprofile-containerized-app.com
cd vprofile-project

2. Start Services Using Docker Compose

```bash
sudo docker compose up -d

3. Verify Running Containers

```bash
sudo docker ps -a

⚙️ Configuration
🔐 Environment Variables

All environment variables are defined in:

db/.env

MYSQL_ROOT_PASSWORD=vprodbpass
MYSQL_DATABASE=accounts

RABBITMQ_DEFAULT_USER=guest
RABBITMQ_DEFAULT_PASS=guest

🧾 Application Properties

Location:

src/main/resources/application.properties

Database Configuration
jdbc:mysql://db01:3306/accounts

Memcached Hosts
mc01
127.0.0.2

RabbitMQ
rmq01:5672

Spring Security Credentials
Username: admin_vp
Password: admin_vp

JSP View Resolver
Prefix: /WEB-INF/views/
Suffix: .jsp

🌐 Accessing the Application
Service	URL
Frontend (vproweb)	http://localhost/

Backend (Tomcat)	http://localhost:8080/

RabbitMQ Management	http://localhost:15672/

MySQL	db01:3306
Memcached	mc01:11211
RabbitMQ Credentials
Username: guest
Password: guest

🛠 Build Details
Application Dockerfile

Multi-stage Docker build

Build stage using:

maven:3.9.9-eclipse-temurin-21-jammy


Runtime stage using:

tomcat:9.0-jdk11-temurin


WAR file deployed as ROOT application

Exposes port 8080

🧩 Docker Compose Services

vprodb → MySQL database

vprocache → Memcached

vpromq → RabbitMQ

vproapp → Java backend (Tomcat)

vproweb → Frontend service

🐞 Notes & Troubleshooting

This is a monolithic application; failure of one service may affect the entire system.

Ensure service hostnames match those in application.properties.

Verify environment variables if database connectivity fails.

View Logs
sudo docker compose logs -f vproapp
sudo docker compose logs -f vprodb

🎯 Learning Outcomes

Containerization of monolithic applications

Multi-container orchestration using Docker Compose

Inter-service communication via Docker networking

Environment-based configuration management

Debugging container startup and connectivity issues

Production-like application deployment


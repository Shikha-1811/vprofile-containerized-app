# VProfile – Dockerized Multi-Container Java Application

## 📌 Overview
VProfile is a monolithic Java web application deployed on Apache Tomcat and fully containerized using **Docker** and **Docker Compose**.  
The application communicates with multiple backend services such as **MySQL**, **Memcached**, and **RabbitMQ**, representing a real-world enterprise setup.

This project demonstrates containerization, service orchestration, inter-service communication, and troubleshooting of a production-like application.

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



🔍 Architecture Explanation
1. Browser (Client)

User accesses the application through a web browser.

Requests are sent to the frontend service over HTTP.

2. vproweb (Frontend – Nginx)

Acts as the reverse proxy / frontend layer.

Serves static content.

Forwards dynamic requests to the backend service (vproapp).

3. vproapp (Backend – Tomcat + Spring MVC)

Core monolithic Java application.

Handles:

Business logic

Authentication

Database operations

Communicates with:

MySQL for persistence

Memcached for caching

RabbitMQ for asynchronous messaging

4. vprodb (MySQL)

Stores application data.

Uses Docker volume for persistent storage.

Accessed only by vproapp.

5. vprocache (Memcached)

Improves performance by caching frequently accessed data.

Reduces database load.

6. vpromq (RabbitMQ)

Handles asynchronous communication and messaging.

Improves scalability and decoupling between components.



---

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
git clone <your-repository-url>
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


<<<<<<< HEAD
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
=======
��� VProfile – Containerized Multi-Tier Java Application (Docker & Docker Compose)
��� Project Overview

VProfile is a multi-tier monolithic Java web application deployed using Docker and Docker Compose.
This project demonstrates how a real-world enterprise application can be containerized and orchestrated using multiple backend services.

⚠️ Important Note (Transparency for Recruiters):
The application source code and dependencies are cloned from the well-known VProfile project, which is widely used for DevOps hands-on practice.
The containerization, service orchestration, environment configuration, and deployment setup are implemented and customized by me.

���️ Architecture
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
            --------------       | ---------------
           v                      v               v
     +-----------+        +---------------+   +-----------+
     | vprodb    |        | vprocache     |   | vpromq    |
     | MySQL     |        | Memcached     |   | RabbitMQ  |
     +-----------+        +---------------+   +-----------+

��� Tech Stack

Backend: Java, Spring MVC, Apache Tomcat

Frontend: JSP

Database: MySQL

Caching: Memcached

Messaging: RabbitMQ

Containerization: Docker

Orchestration: Docker Compose

��� Project Structure
vprofile-project/
│
├── app/                 # Application Dockerfile
├── web/                 # Frontend service
├── db/                  # MySQL configs & .env
├── src/                 # Java source code
├── docker-compose.yml   # Multi-container orchestration
└── README.md

⚙️ Prerequisites

Docker

Docker Compose

Git

Minimum 4 GB RAM

��� Setup & Deployment
1️⃣ Clone Repository
git clone <your-repository-url>
cd vprofile-project

2️⃣ Start Services Using Docker Compose
sudo docker compose up -d

3️⃣ Verify Running Containers
sudo docker ps -a

��� Configuration
��� Environment Variables

Location: db/.env
>>>>>>> e8512a4 (Updated professional README)

MYSQL_ROOT_PASSWORD=vprodbpass
MYSQL_DATABASE=accounts

RABBITMQ_DEFAULT_USER=guest
RABBITMQ_DEFAULT_PASS=guest

<<<<<<< HEAD
🧾 Application Properties

Location:

src/main/resources/application.properties

Database Configuration
jdbc:mysql://db01:3306/accounts

Memcached Hosts
=======
⚙️ Application Properties

Location: src/main/resources/application.properties

Database
jdbc:mysql://db01:3306/accounts

Memcached
>>>>>>> e8512a4 (Updated professional README)
mc01
127.0.0.2

RabbitMQ
rmq01:5672

<<<<<<< HEAD
Spring Security Credentials
=======
Spring Security
>>>>>>> e8512a4 (Updated professional README)
Username: admin_vp
Password: admin_vp

JSP View Resolver
Prefix: /WEB-INF/views/
Suffix: .jsp

<<<<<<< HEAD
🌐 Accessing the Application
=======
��� Accessing the Application
>>>>>>> e8512a4 (Updated professional README)
Service	URL
Frontend (vproweb)	http://localhost/

Backend (Tomcat)	http://localhost:8080/

RabbitMQ Management	http://localhost:15672/

MySQL	db01:3306
Memcached	mc01:11211
RabbitMQ Credentials
Username: guest
Password: guest

<<<<<<< HEAD
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
=======
��� Build Details
Dockerfile (Application)

Multi-stage Docker build

Build Stage:
maven:3.9.9-eclipse-temurin-21-jammy

Runtime Stage:
tomcat:9.0-jdk11-temurin

WAR deployed to Tomcat

Port 8080 exposed

Docker Compose Services

vprodb → MySQL
>>>>>>> e8512a4 (Updated professional README)

vprocache → Memcached

vpromq → RabbitMQ

<<<<<<< HEAD
vproapp → Java backend (Tomcat)

vproweb → Frontend service

🐞 Notes & Troubleshooting

This is a monolithic application; failure of one service may affect the entire system.

Ensure service hostnames match those in application.properties.

Verify environment variables if database connectivity fails.

=======
vproapp → Java / Tomcat backend

vproweb → Frontend service

���️ Logs & Troubleshooting
>>>>>>> e8512a4 (Updated professional README)
View Logs
sudo docker compose logs -f vproapp
sudo docker compose logs -f vprodb

<<<<<<< HEAD
🎯 Learning Outcomes

Containerization of monolithic applications

Multi-container orchestration using Docker Compose

Inter-service communication via Docker networking

Environment-based configuration management

Debugging container startup and connectivity issues

Production-like application deployment
=======
Common Issues

MySQL container fails

Verify .env credentials

Check container logs

RabbitMQ UnknownHost

Ensure hostname rmq01 matches application.properties
>>>>>>> e8512a4 (Updated professional README)


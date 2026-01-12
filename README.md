# VProfile Project

## Overview

**VProfile** is a monolithic Java web application deployed on **Apache Tomcat**.  
It provides a frontend web interface (`vproweb`) and communicates with backend services including **MySQL**, **Memcached**, and **RabbitMQ**.

All components are tightly coupled; if one service fails, the application may not function correctly.

---

## Architecture


# Book Catalog - A Full-Stack Microservices Project

Welcome to the central hub for the Book Catalog project! This repository contains the high-level architectural documentation and serves as the main entrypoint for understanding the entire ecosystem.

This project is a practical exercise in designing, building, testing, and deploying a distributed application using modern DevOps principles and a cloud-native approach.

## 🏛️ Architecture Overview

The ecosystem is built upon a multi-repo, microservices architecture. Each core component of the application lives in its own dedicated repository, allowing for independent development, testing, and deployment cycles.

The main components are:

- **📖 [book-catalog](https://github.com/DanLearnings/book-catalog):** (You are here) The main entrypoint and architectural documentation hub.
- **⚙️ [book-catalog-api](https://github.com/DanLearnings/book-catalog-api):** The backend API responsible for all business logic and data persistence.
- **🖥️ [book-catalog-frontend](https://github.com/DanLearnings/book-catalog-frontend):** The frontend web application that users interact with.
- **🚀 [book-catalog-orchestration](https://github.com/DanLearnings/book-catalog-orchestration):** The orchestration layer responsible for running the entire application stack using Docker Compose and managing CI/CD pipelines via GitHub Actions.

## 🛠️ Tech Stack

- **Backend:** Java 21, Spring Boot 3
- **Frontend:** Angular
- **Database:** PostgreSQL
- **Containerization:** Docker
- **Orchestration & CI/CD:** Docker Compose, GitHub Actions, GitHub Container Registry

## 🚀 Getting Started

*Instructions on how to run the entire ecosystem locally will be added to the `book-catalog-orchestration` repository in the future.*

---

*This project is currently under active development. You can follow the progress on our [GitHub Project Board]([LINK-TO-YOUR-PROJECT-BOARD](https://github.com/orgs/DanLearnings/projects/1/views/1)).*

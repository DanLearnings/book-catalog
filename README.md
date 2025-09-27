# Book Catalog - A Full-Stack DevOps Project Journey

Welcome to the central hub for the Book Catalog project! This repository contains the high-level architectural documentation and serves as the main entrypoint for understanding the entire ecosystem.

This project was a practical exercise that I undertook to design, build, test, and deploy a full-stack web application using modern DevOps principles. This document outlines the architecture, the technology stack, and the journey through each phase of development, highlighting key lessons learned along the way.

You can follow the project's progress and tasks on the [**GitHub Project Board**](https://github.com/orgs/DanLearnings/projects/1/views/1).

## 🏛️ Architecture Overview

The ecosystem is built upon a **multi-repo architecture**, not a microservices one. This choice was made to decouple the development lifecycle of the frontend and backend, allowing them to evolve independently.

The main components are:

-   **📖 [book-catalog](https://github.com/DanLearnings/book-catalog):** (You are here) The main entrypoint and architectural documentation hub.
-   **⚙️ [book-catalog-api](https://github.com/DanLearnings/book-catalog-api):** A modular monolithic backend API responsible for all business logic and data persistence.
-   **🖥️ [book-catalog-frontend](https://github.com/DanLearnings/book-catalog-frontend):** A Single Page Application (SPA) that users interact with.
-   **🚀 [book-catalog-orchestration](https://github.com/DanLearnings/book-catalog-orchestration):** The orchestration layer responsible for running the entire application stack using Docker Compose (for local development) and Kubernetes manifests (for production).

## 🛠️ Tech Stack

-   **Backend:** Java 21, Spring Boot 3
-   **Frontend:** Angular (Standalone Components)
-   **Database:** PostgreSQL
-   **Containerization:** Docker
-   **Orchestration & CI/CD:** Docker Compose, Kubernetes, GitHub Actions, GitHub Container Registry

---

## 🚀 The Development Journey & Key Learnings

This project was built iteratively in distinct phases, each with its own challenges and lessons.

### Phase 1: The Foundation (Setup & Architecture)

Before writing any code, I focused on creating a solid organizational structure.

-   **What I did:** Established the `DanLearnings` organization, defined the multi-repo structure, created initial documentation, and set up a Kanban board to manage the project.
-   **💡 Key Learning:** The distinction between a **multi-repo** setup (code organization) and a **microservices** architecture (backend design pattern) became clear. A solid foundation makes the development process much smoother.

### Phase 2: Building the Backend (Initial API)

I developed the backend as a simple, modular monolith.

-   **What I did:** Built a functional RESTful API with Spring Boot for CRUD operations, structured the code into clear layers, created a multi-stage `Dockerfile`, and implemented a CI pipeline with GitHub Actions to automatically build and publish the Docker image to GHCR.
-   **💡 Key Learning:** I learned to debug Docker build issues in minimal environments like Alpine by explicitly setting environment variables (`ENV LANG C.UTF-8`) and realized the importance of using `docker pull` to defeat local image caching during manual tests.

### Phase 3: Building the Frontend (Single Page Application)

I developed the user interface using modern Angular features.

-   **What I did:** Created the project using Standalone Components, built a service to communicate with the backend, and adopted the new `@if`/`@for` control flow syntax. I also dockerized the frontend with Nginx and created its own CI pipeline.
-   **💡 Key Learning:** Debugging the frontend was a deep dive into real-world issues. I solved problems related to CORS (on the backend), Angular's `angular.json` configuration (after removing SSR), and a complex Change Detection issue that required a deep investigation of the component's state.

### Phase 4: Orchestration (Bringing It All Together)

This phase was about making the independent components work as a single, cohesive system.

-   **What I did:**
    1.  **Local Environment:** Created a `docker-compose.yml` file to run the entire stack (API, Frontend, DB) locally with a single command.
    2.  **Production Simulation:** Wrote Kubernetes manifests (`Deployment`, `Service`, `StatefulSet`, `Ingress`) and successfully deployed the entire application to the local Kubernetes cluster provided by Docker Desktop.
-   **💡 Key Learning:** I saw firsthand how orchestrators manage networking, configuration, and data persistence. A crucial lesson was the necessity of setting `imagePullPolicy: Always` in Kubernetes deployments to ensure the latest Docker image is always used.

---

## 🏁 Current Status & Next Steps

The project has successfully reached its initial goal: a fully functional, containerized, and orchestrated full-stack application with an automated CI process.

The next logical steps to evolve this project would be:

1.  **Enhance the Backend:** Add DTOs, global exception handling, and a full suite of unit and integration tests.
2.  **Complete the Frontend:** Implement the full CRUD functionality with forms, routing, and user feedback.
3.  **Implement Continuous Delivery (CD):** Create a final pipeline in the orchestration repository to automatically deploy changes to a real cloud-based Kubernetes cluster.

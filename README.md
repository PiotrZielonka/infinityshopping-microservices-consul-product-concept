# InfinityShopping Microservices – Concept and Demo

This is the **microservices-based concept** of the [InfinityShopping](https://github.com/PiotrZielonka/infinityshopping) e-commerce shop generator, originally implemented as a **monolithic JHipster application**.

The purpose of this repository is to **learn and demonstrate microservices architecture** using **JHipster**, **Spring Boot**, and **Consul**, while offering a solid base for scaling the monolith into a full microservices solution.

---

## 🚀 Project Goals

* Learn JHipster’s microservice architecture by **building from real generated code**.
* Compare service discovery strategies (Spring Cloud **Consul** vs **Eureka**).
* Demonstrate modern DevOps architecture using **Git submodules** for separation of concerns.

---

## ⚙️ Architecture Overview

| Service      | Port   | Description                          |
| ------------ | ------ | ------------------------------------ |
| Gateway      | `8080` | Front door, authentication & routing |
| Store        | `8081` | Basic e-commerce logic (CRUD)        |
| Notification | `8082` | Notification microservice (CRUD)     |
| Consul       | `8500` | Service registry & config server     |

All services are generated using JHipster and can be extended or regenerated using JHipster commands.

---

## 🗃️ Concept of InfinityShopping Microservices Architecture Diagram
This diagram illustrates the concept of InfinityShopping microservices:

![InfinityShopping Microservices](./infinityshopping-microservices.png)

---

## 🔄 Gateway Routing Demo

This GIF shows how the **Gateway at `localhost:8080`** dynamically routes requests to the **Store** and **Notification** microservices:
![Gateway Routing Demo](./infinityshopping-gateway-demo.gif)

---

## 🧱 Microservices Strategy with Git Submodules

Each microservice is stored in its own Git repository and linked here as a **submodule**, allowing for independent development.

### How to use git in submodules:

#### ✅ The command below pulls all microservices at once:

```bash
git clone --recurse-submodules https://github.com/PiotrZielonka/infinityshopping-microservices-consul-product-concept.git
```

> ⚠️ This repository is **not meant for direct commits to microservices**. It’s a wrapper to bring submodules together. To make changes:

1. Go to the specific microservice repo (e.g.[infinityshopping-microservice-consul-store](https://github.com/PiotrZielonka/infinityshopping-microservice-consul-store))
2. Make your changes and commit there:
3. Return to this project and run:

  ```bash
  git submodule update --remote --merge https://github.com/PiotrZielonka/infinityshopping-microservice-consul-store.git
  ```

4. You can also transfer changes from all microservices at once run:
  ```bash
  git submodule update --remote --merge
  ```

---

## 🧪 Running the Application Locally

### Prerequisites

| Tool       | Version           |
| ---------- | ----------------- |
| Docker     | 28.0.4 (Desktop)  |
| Java       | OpenJDK 17        |
| Maven      | 3.8.1             |
| Node.js    | 22.15.1 (x64)     |
| PostgreSQL | Installed locally |

* This project has been tested with Docker Desktop version 28.0.4, but it should work with any newer release.
* Node.js 22.15.1 (x64) is verified to work, but other versions may also be compatible.
* PostgreSQL must be installed locally for database setup and connection.

### Database Setup Instructions

> By default, JHipster configures PostgreSQL in Docker, but **this version connects to a locally installed PostgreSQL instance**.

To make sure you are running with the correct setup:

1. Start Docker (required for some JHipster containers).
2. **Delete any PostgreSQL Docker containers** after startup.

    * This avoids conflict since **local DB connection is used** (not Docker).
3. Make sure the local DB configuration matches these commits or configure database connection:

    * [Gateway DB Config](https://github.com/PiotrZielonka/infinityshopping-consul-gateway/commit/a78424f55258a30ed59372e8554d5ec19483e350)
    * [Store DB Config](https://github.com/PiotrZielonka/infinityshopping-microservice-consul-store/commit/064eeedfe9714114a2d8d5346ae7f895cb0fce06)
    * [Notification DB Config](https://github.com/PiotrZielonka/infinityshopping-microservice-consul-notification/commit/2c4cdfb871243390a84d6f67f35086b6013ebd5f)

### Launch

1. Start the Gateway on `localhost:8080` 
2. Start the Store Microservice on `localhost:8081`   
2. Start the Notification Microservice on `localhost:8082`  
3. In each project directory (gateway, store and notification), run the following command:

```bash
   ./mvnw
````


---

## 📫 Questions?

If you have questions or want to connect:

* Check out the monolith version: [InfinityShopping Monolith](https://github.com/PiotrZielonka/infinityshopping)
* Open an issue on this repository

---

## 🔭 Project Scope

This is a **learning playground** but also a **powerful concept prototype** for real-world microservice systems.


---

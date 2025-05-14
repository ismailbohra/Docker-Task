# MeshCentral Docker Setup with MongoDB Integration

## 📌 Purpose of the Task

Create a Dockerfile for setting up a containerized instance of MeshCentral, with MongoDB as its backend.

## ✅ What I Did

- Created a **Docker Compose** configuration to run:
  - **MongoDB** – to store MeshCentral data persistently.
  - **MeshCentral** – the core remote management server.
  - **Mongo Express** – a web-based interface to monitor the MongoDB database.

- Configured environment variables for secure database authentication.
- Connected all services using a **custom Docker network**.
- Used **named volumes** to ensure data persistence even if containers are stopped or deleted.
- Exposed necessary ports for accessing:
  - MeshCentral dashboard via `https://localhost`
  - Mongo Express via `http://localhost:8081`

## ⚙️ Services Overview

### 1. `mongodb`
- Stores MeshCentral data.
- Runs with a root user `meshcentraladmin` and password `meshcentralpassword`.
- Data stored in a persistent volume `mongodb_data`.

### 2. `mongo-express`
- GUI to monitor and interact with MongoDB.
- Accessible at: `http://localhost:8081`.

### 3. `meshcentral`
- Main remote access server.
- Uses MongoDB as backend (`USE_MONGODB=true`).
- Accessible via:
  - `http://localhost` (auto-redirects to HTTPS)
  - `https://localhost` (main web interface)
  - `https://localhost:4433` (for agent relay)

## 🚀 How to Run

Clone this repository or place the following `docker-compose.yml` in a new directory:

```bash
docker-compose up -d

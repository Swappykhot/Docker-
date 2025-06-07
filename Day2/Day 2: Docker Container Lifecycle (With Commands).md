
# 🚀 Day 2 – Mastering the Docker Container Lifecycle

Understanding how containers move through their lifecycle is key to working efficiently with Docker in real-world DevOps pipelines.

---

## 📊 Docker Lifecycle Overview

```
Dockerfile → Image → Container → Stop/Delete
```

📌 This is the journey every application takes in a Dockerized environment:

- **Dockerfile** – Define your app environment.  
- **Image** – Build a snapshot using `docker build`.  
- **Container** – Create a running instance using `docker run`.  
- **Stopped/Deleted** – Manage the state using `docker stop` or `docker rm`.  

---

![Docker_Container_Lifecycle](https://github.com/user-attachments/assets/6795b6a5-4484-4715-b95f-76602ba4f830)

---

## 🔧 Docker Commands

```bash
# Build an image from Dockerfile
docker build -t myapp:latest .

# Run a container from the image
docker run -d --name myapp_container -p 3000:3000 myapp:latest

# List running containers
docker ps

# Stop a container
docker stop myapp_container

# Remove a container
docker rm myapp_container

# Remove an image
docker rmi myapp:latest
```

💡 **Use `docker inspect` to explore detailed container metadata – super useful in CI/CD pipelines.**

---

## 🧠 Docker Commands Explained 

### 🏗️ Build your app into a Docker Image
```bash
docker build -t myapp:latest .
```
👉 Takes your Dockerfile and builds it into an image named `myapp`.  
✅ `-t` is for tagging the image. `.` means current directory.

---

### 🚀 Run your container from the image
```bash
docker run -d --name myapp_container -p 3000:3000 myapp:latest
```
👉 Starts a new container in the background (`-d`).  
✅ `--name` gives it a name.  
✅ `-p` maps your local port to the container’s port.

---

### 📋 See which containers are running
```bash
docker ps
```
👉 Shows a list of currently running containers.

---

### ⏹️ Stop a running container
```bash
docker stop myapp_container
```
👉 Gracefully stops the container named `myapp_container`.

---

### 🗑️ Delete a container
```bash
docker rm myapp_container
```
👉 Deletes the container from your system (only if it's stopped).

---

### 🧼 Delete an image
```bash
docker rmi myapp:latest
```
👉 Removes the Docker image to free up disk space.

---

### 🔍 Inspect container details
```bash
docker inspect myapp_container
```
👉 Shows low-level details of the container — great for debugging or CI/CD.

---

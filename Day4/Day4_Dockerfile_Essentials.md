# 🚀 Day 4: Dockerfile Essentials





<img src="https://github.com/user-attachments/assets/16968dd0-aca9-4f82-b43e-f7cfe0f72d89" alt="Day4" width="400"/>





Master the core Dockerfile instructions to build efficient Docker images.

---

## 📘 What is a Dockerfile?
A **Dockerfile** is a text file that contains a set of instructions to assemble a Docker image. Each instruction adds a layer to your image and defines how your app runs inside the container.

---

## 📌 Common Dockerfile Instructions

| Instruction | Purpose                                | Example                                |
|-------------|----------------------------------------|----------------------------------------|
| `FROM`      | Sets the base image                    | `FROM node:18`                         |
| `WORKDIR`   | Sets working directory                 | `WORKDIR /app`                         |
| `COPY`      | Copies files into the container        | `COPY . /app`                          |
| `RUN`       | Executes command during build          | `RUN npm install`                      |
| `CMD`       | Sets default container command         | `CMD ["node", "app.js"]`               |
| `EXPOSE`    | Informs about exposed port             | `EXPOSE 3000`                          |
| `ENV`       | Sets environment variables             | `ENV NODE_ENV=production`              |

---

## 💡 Best Practices
- ✅ Pin base image versions to avoid unexpected updates (e.g., `node:18`).
- ✅ Combine `RUN` commands to minimize image layers.
- ✅ Use `.dockerignore` to exclude unnecessary files.
- ✅ Use `CMD` for app start and `ENTRYPOINT` for scripts or containers as services.

---

## ⚠️ Common Errors and Fixes
- `COPY failed`: Ensure the file path exists relative to the Dockerfile.
- `permission denied`: Use `RUN chmod +x script.sh` if required.
- `npm install` fails: Precede with `RUN apt-get update -y && apt-get install -y curl` for missing dependencies.

---

## 🛠️ Mini Project: Dockerize a Simple Node.js App

### 1️⃣ Create `app.js`

```javascript
const http = require("http");
const PORT = 3000;

http.createServer((req, res) => {
  res.end("Hello from Docker!");
}).listen(PORT, () => console.log(`Listening on ${PORT}`));
```

**Explanation:**
- `http.createServer` creates a simple server.
- `res.end(...)` sends a response.
- `listen(...)` starts server on port 3000.

---

### 2️⃣ Create `Dockerfile`

```Dockerfile
# Use official Node.js image as base
FROM node:18

# Set working directory in the container
WORKDIR /app

# Copy current directory files to container's /app
COPY . .

# Install dependencies (if package.json exists)
RUN npm install || true

# Inform Docker to expose port 3000
EXPOSE 3000

# Command to run the app
CMD ["node", "app.js"]
```

**Explanation:**
- `FROM node:18`: Starts from Node.js image.
- `WORKDIR /app`: Sets working directory.
- `COPY . .`: Copies all files into container.
- `RUN npm install`: Installs Node.js dependencies.
- `CMD [...]`: Starts the app when container runs.

---

### 3️⃣ Build and Run the Container

```bash
# Build the Docker image
docker build -t node-docker-app .

# Run the image in a container
docker run -p 3000:3000 node-docker-app
```

Now visit `http://localhost:3000` and you should see: `Hello from Docker!`

---


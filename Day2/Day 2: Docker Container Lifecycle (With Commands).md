
![Docker_Container_Lifecycle](https://github.com/user-attachments/assets/6795b6a5-4484-4715-b95f-76602ba4f830)



Dockerfile → Image → Container → Stop/Delete


📌 This is the journey every application takes in a Dockerized environment:

Dockerfile – Define your app environment.

Image – Build a snapshot using docker build.

Container – Create a running instance using docker run.

Stopped/Deleted – Manage the state using docker stop or docker rm.




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

Use docker inspect to explore detailed container metadata – super useful in CI/CD pipelines.

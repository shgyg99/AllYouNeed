**Docker Cheat Sheet**

---

### **Basic Docker Commands**

- **Check Docker Version:**
  ```
  docker --version
  ```

- **List Available Commands:**
  ```
  docker --help
  ```

- **Start Docker Service:**
  ```
  sudo systemctl start docker
  ```

- **Check Docker Status:**
  ```
  sudo systemctl status docker
  ```

- **Restart Docker Service:**
  ```
  sudo systemctl restart docker
  ```

- **Stop Docker Service:**
  ```
  sudo systemctl stop docker
  ```

---

### **Images**

- **Search for an Image:**
  ```
  docker search <image_name>
  ```

- **Pull an Image:**
  ```
  docker pull <image_name>:<tag>
  ```

- **List All Images:**
  ```
  docker images
  ```

- **Remove an Image:**
  ```
  docker rmi <image_id>
  ```

- **Tag an Image:**
  ```
  docker tag <image_id> <repository>/<image_name>:<tag>
  ```

- **Save an Image to a File:**
  ```
  docker save -o <file_name.tar> <image_name>
  ```

- **Load an Image from a File:**
  ```
  docker load -i <file_name.tar>
  ```

---

### **Containers**

- **Create and Start a Container:**
  ```
  docker run -d --name <container_name> <image_name>
  ```

- **Run a Container Interactively:**
  ```
  docker run -it <image_name> /bin/bash
  ```

- **List Running Containers:**
  ```
  docker ps
  ```

- **List All Containers:**
  ```
  docker ps -a
  ```

- **Stop a Running Container:**
  ```
  docker stop <container_id>
  ```

- **Start a Stopped Container:**
  ```
  docker start <container_id>
  ```

- **Restart a Container:**
  ```
  docker restart <container_id>
  ```

- **Remove a Container:**
  ```
  docker rm <container_id>
  ```

- **Remove All Stopped Containers:**
  ```
  docker container prune
  ```

- **View Logs of a Container:**
  ```
  docker logs <container_id>
  ```

- **Follow Logs of a Running Container:**
  ```
  docker logs -f <container_id>
  ```

- **Access a Running Container:**
  ```
  docker exec -it <container_id> /bin/bash
  ```

- **Export a Container to a File:**
  ```
  docker export <container_id> > <file_name.tar>
  ```

- **Import a Container from a File:**
  ```
  cat <file_name.tar> | docker import - <new_image_name>
  ```

---

### **Volumes**

- **Create a Volume:**
  ```
  docker volume create <volume_name>
  ```

- **List All Volumes:**
  ```
  docker volume ls
  ```

- **Inspect a Volume:**
  ```
  docker volume inspect <volume_name>
  ```

- **Remove a Volume:**
  ```
  docker volume rm <volume_name>
  ```

- **Remove All Unused Volumes:**
  ```
  docker volume prune
  ```

- **Mount a Volume to a Container:**
  ```
  docker run -v <volume_name>:<container_path> <image_name>
  ```

---

### **Networking**

- **List Docker Networks:**
  ```
  docker network ls
  ```

- **Inspect a Network:**
  ```
  docker network inspect <network_name>
  ```

- **Create a Network:**
  ```
  docker network create <network_name>
  ```

- **Remove a Network:**
  ```
  docker network rm <network_name>
  ```

- **Run a Container with a Specific Network:**
  ```
  docker run --network <network_name> <image_name>
  ```

- **Connect a Container to a Network:**
  ```
  docker network connect <network_name> <container_name>
  ```

- **Disconnect a Container from a Network:**
  ```
  docker network disconnect <network_name> <container_name>
  ```

---

### **Docker Compose**

- **Start Services in `docker-compose.yml`:**
  ```
  docker-compose up
  ```

- **Start Services in Detached Mode:**
  ```
  docker-compose up -d
  ```

- **Stop Services:**
  ```
  docker-compose down
  ```

- **View Running Services:**
  ```
  docker-compose ps
  ```

- **Restart Services:**
  ```
  docker-compose restart
  ```

- **Build or Rebuild Services:**
  ```
  docker-compose build
  ```

- **Run a One-Time Command:**
  ```
  docker-compose run <service_name> <command>
  ```

- **Remove Volumes Used by Services:**
  ```
  docker-compose down --volumes
  ```

---

### **Clean Up**

- **Remove All Stopped Containers:**
  ```
  docker container prune
  ```

- **Remove All Unused Volumes:**
  ```
  docker volume prune
  ```

- **Remove All Unused Images:**
  ```
  docker image prune
  ```

- **Remove All Unused Data:**
  ```
  docker system prune
  ```

- **Force Remove All Unused Data (including volumes):**
  ```
  docker system prune -a --volumes
  ```

---

### **Dockerfile Basics**

- **Common Instructions:**
  ```Dockerfile
  FROM <base_image>
  WORKDIR /app
  COPY . .
  RUN <command_to_install_dependencies>
  EXPOSE 8080
  CMD ["executable", "arg1", "arg2"]
  ```

- **Build an Image:**
  ```
  docker build -t <image_name> .
  ```

- **Run a Container from Dockerfile:**
  ```
  docker run <image_name>
  ```

- **Cache Busting Example:**
  ```Dockerfile
  ARG CACHEBUST=1
  RUN echo $CACHEBUST
  ```

---

### **Best Practices**

- **Use Small Base Images:**
  Prefer `alpine` or other minimal base images to reduce image size.

- **Use Multi-Stage Builds:**
  ```Dockerfile
  # Build Stage
  FROM golang:1.17 AS builder
  WORKDIR /app
  COPY . .
  RUN go build -o main .

  # Production Stage
  FROM alpine:latest
  WORKDIR /root/
  COPY --from=builder /app/main .
  CMD ["./main"]
  ```

- **Reduce Layers:**
  Combine `RUN` instructions to reduce the number of image layers.

- **Avoid Using `latest` Tag:**
  Specify the exact image version to ensure consistent builds.

---


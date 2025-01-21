# 🐳 **Docker Cheat Sheet**

---

## 🎯 **Basic Docker Commands**

- **Check Docker Version:**
  ```bash
  docker --version
  ```
- **List Available Commands:**
  ```bash
  docker --help
  ```
- **Start Docker Service:**
  ```bash
  sudo systemctl start docker
  ```
- **Check Docker Status:**
  ```bash
  sudo systemctl status docker
  ```
- **Restart Docker Service:**
  ```bash
  sudo systemctl restart docker
  ```
- **Stop Docker Service:**
  ```bash
  sudo systemctl stop docker
  ```

---

## 📦 **Images**

- **Search for an Image:**
  ```bash
  docker search <image_name>
  ```
- **Pull an Image:**
  ```bash
  docker pull <image_name>:<tag>
  ```
- **List All Images:**
  ```bash
  docker images
  ```
- **Remove an Image:**
  ```bash
  docker rmi <image_id>
  ```
- **Tag an Image:**
  ```bash
  docker tag <image_id> <repository>/<image_name>:<tag>
  ```
- **Save an Image to a File:**
  ```bash
  docker save -o <file_name.tar> <image_name>
  ```
- **Load an Image from a File:**
  ```bash
  docker load -i <file_name.tar>
  ```

---

## 🛠 **Containers**

- **Create and Start a Container:**
  ```bash
  docker run -d --name <container_name> <image_name>
  ```
- **Run a Container Interactively:**
  ```bash
  docker run -it <image_name> /bin/bash
  ```
- **List Running Containers:**
  ```bash
  docker ps
  ```
- **List All Containers:**
  ```bash
  docker ps -a
  ```
- **Stop a Running Container:**
  ```bash
  docker stop <container_id>
  ```
- **Start a Stopped Container:**
  ```bash
  docker start <container_id>
  ```
- **Restart a Container:**
  ```bash
  docker restart <container_id>
  ```
- **Remove a Container:**
  ```bash
  docker rm <container_id>
  ```
- **Remove All Stopped Containers:**
  ```bash
  docker container prune
  ```
- **View Logs of a Container:**
  ```bash
  docker logs <container_id>
  ```
- **Follow Logs of a Running Container:**
  ```bash
  docker logs -f <container_id>
  ```
- **Access a Running Container:**
  ```bash
  docker exec -it <container_id> /bin/bash
  ```
- **Export a Container to a File:**
  ```bash
  docker export <container_id> > <file_name.tar>
  ```
- **Import a Container from a File:**
  ```bash
  cat <file_name.tar> | docker import - <new_image_name>
  ```

---

## 📂 **Volumes**

- **Create a Volume:**
  ```bash
  docker volume create <volume_name>
  ```
- **List All Volumes:**
  ```bash
  docker volume ls
  ```
- **Inspect a Volume:**
  ```bash
  docker volume inspect <volume_name>
  ```
- **Remove a Volume:**
  ```bash
  docker volume rm <volume_name>
  ```
- **Remove All Unused Volumes:**
  ```bash
  docker volume prune
  ```
- **Mount a Volume to a Container:**
  ```bash
  docker run -v <volume_name>:<container_path> <image_name>
  ```

---

## 🌐 **Networking**

- **List Docker Networks:**
  ```bash
  docker network ls
  ```
- **Inspect a Network:**
  ```bash
  docker network inspect <network_name>
  ```
- **Create a Network:**
  ```bash
  docker network create <network_name>
  ```
- **Remove a Network:**
  ```bash
  docker network rm <network_name>
  ```
- **Run a Container with a Specific Network:**
  ```bash
  docker run --network <network_name> <image_name>
  ```
- **Connect a Container to a Network:**
  ```bash
  docker network connect <network_name> <container_name>
  ```
- **Disconnect a Container from a Network:**
  ```bash
  docker network disconnect <network_name> <container_name>
  ```

---

## 📜 **Docker Compose**

- **Start Services in `docker-compose.yml`:**
  ```bash
  docker-compose up
  ```
- **Start Services in Detached Mode:**
  ```bash
  docker-compose up -d
  ```
- **Stop Services:**
  ```bash
  docker-compose down
  ```
- **View Running Services:**
  ```bash
  docker-compose ps
  ```
- **Restart Services:**
  ```bash
  docker-compose restart
  ```
- **Build or Rebuild Services:**
  ```bash
  docker-compose build
  ```
- **Run a One-Time Command:**
  ```bash
  docker-compose run <service_name> <command>
  ```
- **Remove Volumes Used by Services:**
  ```bash
  docker-compose down --volumes
  ```

---

## 🧹 **Clean Up**

- **Remove All Stopped Containers:**
  ```bash
  docker container prune
  ```
- **Remove All Unused Volumes:**
  ```bash
  docker volume prune
  ```
- **Remove All Unused Images:**
  ```bash
  docker image prune
  ```
- **Remove All Unused Data:**
  ```bash
  docker system prune
  ```
- **Force Remove All Unused Data (including volumes):**
  ```bash
  docker system prune -a --volumes
  ```

---

## 🛠️ **Dockerfile Basics**

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
  ```bash
  docker build -t <image_name> .
  ```
- **Run a Container from Dockerfile:**
  ```bash
  docker run <image_name>
  ```
- **Cache Busting Example:**
  ```Dockerfile
  ARG CACHEBUST=1
  RUN echo $CACHEBUST
  ```

---

## 🌟 **Best Practices**

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

🌐 **Happy Dockerizing!** 🚀


# Docker Command Cheat Sheet

A list of essential docker commands - to help streamline the workflow process when working with Docker.

Detailed with examples/templates - to enhance quick comprehension - especially when returning to Docker after a while without using it.

> **Most frequently used commands appear top-most.**
> Replace placeholders like `image-name`, `container-name`, `path/to/context`, etc., with your actual values.

---

## 🔨 1. Build a Docker Image

```bash
docker build -t image-name path/to/context
```

Example:

```bash
docker build -t my-image ./child-directory
```

or

```bash
docker build -t my-image . # a period indicates that the dockerfile to build from is in the current directory where the command is being run
```

---

## 📄 2. Build Image with a Specific Dockerfile

```bash
docker build -f path/to/Dockerfile -t image-name:tag path/to/context
```

Example

```bash
docker build -f ./learning-jenkins/Dockerfile.jenkins_nodejs_python -t jenkins_nodejs_python_agent:latest ./learning-jenkins/
```

---

## 🏷️ 3. Tag a Docker Image

```bash
docker image tag image-name image-name:new-tag
docker image tag image-name username/image-name:tag
```

---

## 📤 4. Push Image to Docker Hub

```bash
docker image push docker-hub-user-name/image-name:tag-name
```

---

## 🧠 5. Run Bash Inside a Container

```bash
docker exec -it container-id bash
docker exec -u root -it container-id bash  # as root
```

---

## 🔍 6. Inspect Container Details

```bash
docker inspect container-id
```

---

## 🚀 7. Run a Container from Local Image

```bash
docker run -d -p desired-port:docker-port -e SECRET_ONE="secret_one" -e SECRET_TWO="secret_two" --name
container-name local-image-name
```
---

## ☁️ 8. Run Container from Remote Image

```bash
docker run -d -p desired-port:docker-port -e SECRET_ONE="secret_one" SECRET_TWO="secret_two" --name container-name
docker-hub-user-name/remote-image-name:tag-name
```

---

## 🔐 9. Use `.env` File for Environment Variables

```bash
docker run -d -p desired-port:docker-port --env-file .env --name container-name local-image-name
```

---

## 🛑 10. Stop and Remove Containers

```bash
docker stop container-name
docker rm container-name
```

---

## 🧹 11. Remove Images, Volumes, and Networks

```bash
docker rmi image-name
docker volume rm volume-name
docker network rm network-name
```

---

## 🧼 12. Clean Up Unused Docker Resources

```bash
docker system prune -a
```

---

## 📦 13. List Everything

```bash
docker ps -a            # all containers
docker images           # all images
docker volume ls        # volumes
docker network ls       # networks
```

---

## 🔁 14. Rebuild and Restart Containers with Docker Compose

```bash
docker-compose down
docker-compose build --no-cache
docker-compose up -d
```

---

## 🧪 15. Run One-Off Commands in Containers

```bash
docker run --rm -it image-name bash
```

---

## 📂 16. Mount a Local Volume (bind mount)

```bash
docker run -v $(pwd):/app -w /app image-name
```

---

## 📄 17. View Container Logs

```bash
docker logs container-name
docker logs -f container-name     # follow logs
```

---

## 🔗 18. Copy Files To/From Containers

```bash
docker cp localfile.txt container-id:/app/
docker cp container-id:/app/file.txt ./
```

---

## 🛠️ 19. Rename Containers or Images

```bash
docker rename old-container-name new-name
docker tag old-image-name new-name:tag
```

---

## 🧰 20. Create a Docker Volume and Use It

```bash
docker volume create my-volume
docker run -v my-volume:/data my-image
```

---

## 🧭 21. Connect to a Container via SSH-like TTY

```bash
docker exec -it container-name sh
```

---

## 🔧 22. Remove All Stopped Containers

```bash
docker container prune
```

---

## 🧊 23. Save and Load Docker Images

```bash
docker save image-name > image.tar
docker load < image.tar
```

---

## 📦 24. Export and Import Containers

```bash
docker export container-id > container.tar
docker import container.tar
```

---

## 🧪 25. Test Dockerfile without Caching

```bash
docker build --no-cache -t image-name .
```

---

## 🧪 26. View Container Environment Variables

```bash
docker exec -it container-name env
```

---


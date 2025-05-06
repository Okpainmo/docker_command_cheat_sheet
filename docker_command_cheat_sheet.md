# Docker Command Cheat Sheet.

Relevant Docker commands, with template samples of how I use some of them.

> P.S: Most used docker commands should appear top-most.

## 1. Build a docker image.

```bash
docker build -t image-name path/to/context
```

e.g

```bash
docker build -t my-image ./child-directory
```

or

```bash
docker build -t my-image . # a period indicates that the dockerfile to build from is in the current directory where the command is being run
```

## 2. Build a docker image selecting the docker file.

```bash
docker build -f path/to/Dockerfile -t your-image-name:tag path/to/context
```

e.g

```bash
docker build -f ./learning-jenkins/Dockerfile.jenkins_nodejs_python -t jenkins_nodejs_python_agent:latest ./learning-jenkins/
```

## 3. Add a tag to a docker image.

```bash
docker image tag image-name image-name:tag-name
```

or

```bash
docker image tag image-name docker-hub-user-name/image-name:tag-name
```

## 4. Push a docker image to docker hub.

```bash
docker image push docker-hub-user-name/image-name:tag-name
```

## 5. execute a bash bash for a running commands on a container

```bash
docker exec -it container-id bash

# as root user below

docker exec -u root -it container-name bash
```

## 6. Inspect a Docker container to see important details - e.g. the container IP, and a lot more.

```bash
docker inspect container-id
```

## 7. Run a docker container(from a locally available image).

```bash
docker run -d -p desired-port:docker-port -e SECRET_ONE="secret_one" -e SECRET_TWO="secret_two" --name
container-name local-image-name
```

## 8. Run a docker container(from a remote image).

```bash
docker run -d -p desired-port:docker-port -e SECRET_ONE="secret_one" SECRET_TWO="secret_two" --name container-name
docker-hub-user-name/remote-image-name:tag-name
```

## 9. Run a docker container(from a remote image) using a local env file(cleaner and more secure)

```bash
docker run -d -p desired-port:docker-port --env-file .env --name container-name local-image-name
```

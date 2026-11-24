# Docker Fundamentals — Beginner Notes

## 1. What is Docker?

Docker is a platform used to package and run applications in **containers**.

It helps an application run more consistently across different computers and servers.

Docker is used for:
- Hosting websites and APIs
- Running databases and background jobs
- Testing applications
- Packaging and deploying AI applications

## 2. Image vs. Container

- **Image:** A packaged, read-only template containing an application and what it needs to run.
- **Container:** An instance created from an image. It can be running or stopped.
- **Docker:** The tools that build images and create and manage containers.

**Remember:** One image can be used to create many containers.

Example: `hello-world` is an image. Running it twice normally creates two separate containers.

## 3. How Docker works

1. Get an image from a registry, such as Docker Hub, or build one.
2. Run the image to create a container.
3. The application runs inside the container.
4. When its main process finishes, the container stops.
5. A stopped container can still be listed with `docker ps -a`.

## 4. Why use Docker?

- **Consistency:** Package application dependencies and runtime together.
- **Portability:** Run the same image in compatible Docker environments.
- **Isolation:** Keep application processes and filesystems separated.
- **Repeatability:** Create similar environments for development, testing, and deployment.
- **Deployment:** Package websites, APIs, and AI services.

Docker does not automatically publish an application to the internet. Hosting also requires a suitable server/platform and network configuration.

## 5. Important terms

- **Docker CLI:** The command-line tool where you type Docker commands.
- **Docker Engine:** Runs and manages containers and images.
- **Dockerfile:** Text file with instructions to build an image.
- **Registry:** Stores and distributes images (for example, Docker Hub).
- **Volume:** Stores data separately from a container's writable layer.
- **Port mapping:** Connects a host port to a container port.
- **Docker Compose:** Tool for defining and running applications with multiple containers.

## 6. Beginner commands

| Command | What it does |
|---|---|
| `docker version` | Shows Docker client and server version information |
| `docker --help` | Shows available Docker commands |
| `docker images` | Lists local images |
| `docker pull hello-world` | Downloads the image |
| `docker run hello-world` | Creates and runs a new container from the image |
| `docker ps` | Lists running containers |
| `docker ps -a` | Lists all containers, including stopped ones |
| `docker logs CONTAINER` | Shows captured output from a container |
| `docker stop CONTAINER` | Stops a running container |
| `docker start CONTAINER` | Starts an existing stopped container |
| `docker build -t my-app .` | Builds an image using a Dockerfile in the current directory |

Replace `CONTAINER` with a container name or ID.

## 7. Understand `hello-world`

Command:

```bash
docker run hello-world
```

Docker uses the `hello-world` image, creates a container, runs its program, and prints a message.

Example container status:

```text
Exited (0)
```

This means the main program finished successfully. The container stopped because `hello-world` is designed to finish, not run continuously.

Use:

```bash
docker ps -a
```

to see stopped containers.

## 8. `docker run` vs. `docker start`

- `docker run IMAGE` normally creates a **new container** and starts it.
- `docker start CONTAINER` starts an **existing stopped container**.

Running `docker run hello-world` multiple times normally creates multiple containers from the same image.

## 9. Website example

A website might run in an Nginx container, while its backend API runs in a separate Python container.

Example command for a real Docker environment:

```bash
docker run -d -p 8080:80 --name my-web nginx
```

- `-d`: run in the background
- `-p 8080:80`: map host port 8080 to container port 80
- `--name my-web`: assign a container name
- `nginx`: image to use

If the environment exposes the port, visit `http://localhost:8080`.

Docker Dojo is a simulation, so some commands or networking features may behave differently from real Docker.

## 10. Quick memory aid

- **Image = template**
- **Container = instance of an image**
- **Dockerfile = instructions to build an image**
- **Registry = place to store and download images**
- **Volume = persistent data storage**
- **`docker ps` = running containers**
- **`docker ps -a` = all containers**

## 11. Beginner practice checklist

- [ ] Run `docker version`
- [ ] Run `docker images`
- [ ] Run `docker run hello-world`
- [ ] Run `docker ps`
- [ ] Run `docker ps -a`
- [ ] Explain why `hello-world` containers stop
- [ ] Explain the difference between an image and a container

**Learning tip:** For every command, understand what it does and inspect the output. Do not only memorize the syntax.


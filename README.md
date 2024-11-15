
# Alian hub - Docker Setup Guide

This document provides all the steps required to set up, build, and run a Docker container for **Alian hub**.

## Prerequisites

- **Docker**: Make sure Docker is installed on your machine. [Download Docker here](https://docs.docker.com/get-docker/).

## Setup Instructions

### 1. Configure Environment Variables

> **Note**: If you have already configured the environment variables and set up the necessary files, you can skip this step.

#### Environment Variables Setup

To manage environment variables, follow the steps below to create and configure `.env` files in the necessary directories. Each part of the application (root, admin, and frontend) requires a separate `.env` file to store its specific environment variables.

> **Note**: Before this Please check .env.example file in root directory.

## Steps

1. **Root Directory**  
   - Create a `.env` file at the root level of the project (`/.env`).
   - This file will contain environment variables used by the main server.

   Example:
   ```plaintext
   # /.env
   API_URL=localhost
   PORT=4000

2. **Admin Directory**
   - Inside the admin directory, create an .env file (/admin/.env).
   - Use this file to specify environment variables needed by the admin portal.

3. **Frontend Directory**
   - Inside the frontend directory, create an .env file (/frontend/.env).
   - Use this file to specify environment variables needed by the frontend portal.

### 3. Build the Docker Image

Run the following command to build the Docker image, loading environment variables from the `.env` file:

```bash
docker build -t your-image-name .
```

Replace `your-image-name` with your desired image name.

### 4. Run the Docker Container

Once the image is built, you can start the Docker container using the following command:

```bash
docker run -d -p 4000:4000 --name your-container-name your-image-name
```

This command will:

- Run the container in detached mode (`-d`)
- Map port 4000 of the container to port 4000 on the host (`-p 4000:4000`)
- Name the container as specified in `your-container-name`

Replace `your-container-name` and `your-image-name` with your preferred container and image names, respectively.

### 5. Verify the Container

To check if the container is running correctly, use the following command:

```bash
docker ps
```

You should see your container in the list. To view logs and troubleshoot, use:

```bash
docker logs your-container-name
```

### 6. Stop and Remove the Container (Optional)

When you're done, stop and remove the container:

```bash
docker stop your-container-name
docker rm your-container-name
```
---

## Docker with Docker compose
You can change container and image name in docker-compose.yml file.

To build image and run container:
```bash
docker-compose up --build -d
```

To stop the containers:
```bash
docker-compose down
```

To rebuild the image:
```bash
docker-compose build
```

To check the status of the running containers:
```bash
docker-compose ps
```
---

## Summary of Commands

Here's a quick summary of the key commands:

```bash
# Build the Docker image with .env
docker build -t your-image-name .

# Run the Docker container
docker run -d -p 4000:4000 --name your-container-name your-image-name

# Check running containers
docker ps

# View container logs
docker logs your-container-name

# Stop and remove container
docker stop your-container-name
docker rm your-container-name

# Docker with Docker Compose file
docker-compose up --build -d
docker-compose build
docker-compose down
docker-compose ps
```

---

That's it! You now have a full guide for setting up, building, and running your Docker container for **Alian hub**.

---

# Docker Container and Image Management

After building your Docker image and running your container, you might want to **stop** and **remove** them. Below are the steps to do so.

## 1. **Stop and Remove the Running Docker Container**

To stop a running container, use the following command:

```bash
docker stop <container_name_or_id>
```

For example:
```bash
docker stop my-app-container
```

Once the container is stopped, you can remove it using the command:

```bash
docker rm <container_name_or_id>
```

For example:
```bash
docker rm my-app-container
```

If you want to **stop and remove** the container in one command, you can do:

```bash
docker rm -f <container_name_or_id>
```

### 2. **Remove the Docker Image**

To remove a Docker image after it has been built, use the following command:

```bash
docker rmi <image_name_or_id>
```

For example:
```bash
docker rmi my-app-image
```

If you have multiple tags or versions of an image, you might want to remove them all. You can use the `-f` (force) flag to force the removal of the image even if there are existing containers associated with it.

```bash
docker rmi -f <image_name_or_id>
```

### 3. **List All Containers and Images**

To check which containers and images are currently available on your system, use the following commands:

- **List all containers (including stopped ones):**
  ```bash
  docker ps -a
  ```

- **List all images:**
  ```bash
  docker images
  ```

### Example

1. Stop and remove the container:
   ```bash
   docker stop my-app-container
   docker rm my-app-container
   ```

2. Remove the Docker image:
   ```bash
   docker rmi my-app-image
   ```
---

## Resources
https://docs.docker.com/reference/cli/docker/

https://docs.docker.com/reference/cli/docker/compose/

https://www.geeksforgeeks.org/docker-instruction-commands/

https://docs.docker.com/get-started/docker_cheatsheet.pdf


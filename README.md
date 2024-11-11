
# Project Name - Docker Setup Guide

This document provides all the steps required to set up, build, and run a Docker container for **Project Name**.

## Prerequisites

- **Docker**: Make sure Docker is installed on your machine. [Download Docker here](https://docs.docker.com/get-docker/).

## Setup Instructions

### 1. Clone the Repository

First, clone the repository to get access to the Dockerfile and project files.

```bash
git clone https://github.com/username/repository-name.git
cd repository-name
```

### 2. Configure Environment Variables

To manage environment variables, create a `.env` file in the root directory of the project. This file will store the required environment variables for the application.

1. Create a file named `.env` in the project root.
2. Add your environment variables to this file in the following format:

```env
# .env file example
ENV_VAR1=value1
ENV_VAR2=value2
# Add more variables as needed
```

Alternatively, if you prefer not to use a `.env` file, you can pass environment variables as `--build-arg` parameters during the Docker build command (not recommended for a large number of variables).

### 3. Build the Docker Image

Run the following command to build the Docker image, loading environment variables from the `.env` file:

```bash
docker build --env-file .env -t your-image-name .
```

Replace `your-image-name` with your desired image name.

#### Optional: Build with Arguments (Without `.env` File)

If you prefer to specify environment variables directly, you can use the `--build-arg` option as shown below. This can be useful for quick builds but is less manageable with numerous variables.

```bash
docker build -t your-image-name --build-arg ENV_VAR1=value1 --build-arg ENV_VAR2=value2 .
```

### 4. Run the Docker Container

Once the image is built, you can start the Docker container using the following command:

```bash
docker run -d -p 4000:4000 --env-file .env --name your-container-name your-image-name
```

This command will:

- Run the container in detached mode (`-d`)
- Map port 4000 of the container to port 4000 on the host (`-p 4000:4000`)
- Load environment variables from the `.env` file
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

## Summary of Commands

Here's a quick summary of the key commands:

```bash
# Clone the repository
git clone https://github.com/username/repository-name.git
cd repository-name

# Build the Docker image with .env
docker build --env-file .env -t your-image-name .

# Run the Docker container
docker run -d -p 4000:4000 --env-file .env --name your-container-name your-image-name

# Check running containers
docker ps

# View container logs
docker logs your-container-name

# Stop and remove container
docker stop your-container-name
docker rm your-container-name
```

---

That's it! You now have a full guide for setting up, building, and running your Docker container for **Project Name**.

# Docker Image Hosting Guide

This document provides the steps to build, host, and manage Docker images for your project.

## Prerequisites

Before starting, ensure that you have the following:

- **Docker** installed on your local machine: [Download Docker here](https://docs.docker.com/get-docker/)
- **Docker Hub Account** (or a private registry if using one)

## Steps

### 1. Build the Docker Image

**1. To create a Docker image for your project, use the following command from the project directory:**

```bash
docker build -t your-image-name .
```
Replace your-image-name with your desired image name. This command will:

- Use the Dockerfile in the current directory to build the image
- Tag the image with the specified name

**2. Tagging the Image**
If you want to tag your image with a version or other identifier (e.g., v1, latest), use the following:

```bash
docker tag your-image-name your-dockerhub-username/your-image-name:v1
```
This will create a new tag v1 for your image.

**3. Log in to Docker Hub**
Before pushing an image to Docker Hub, ensure you're logged in:

```bash
docker login
```
Enter your Docker Hub credentials when prompted, or simply go to the activation route and add the code displayed in the terminal.

**4. Push the Image to Docker Hub**
Once your image is built and tagged, push it to Docker Hub (or your private registry) using the following command:
```bash
docker push your-dockerhub-username/your-image-name:v1
```

**5. Hosting Docker Image on a Private Registry (Optional)**
If you're using a private registry (e.g., AWS ECR, Google Container Registry), follow the provider's documentation to:
- Set up a registry (e.g., create a repository in AWS ECR).
- Authenticate to the registry.
- Push the image to the private registry.

```bash
# Tag the image
docker tag your-image-name your-private-registry-url/your-image-name:v1
# Push the image
docker push your-private-registry-url/your-image-name:v1
```

> **Note**: Make sure port is 4000.

That's it! You now have a complete guide for pushing a Docker image to any image registry. You can now use this image and deploy it.

---

## For checking the Docker image locally
**1. Pull the Docker Image from Docker Hub**
To pull the image from Docker Hub or a private registry, use:
```bash
docker pull your-dockerhub-username/your-image-name:v1
```
For a private registry, use:
```bash
docker pull your-private-registry-url/your-image-name:v1
```

**2. Run the Docker Image**
Once the image is pulled, run the container using:
```bash
docker run -d -p 4000:4000 --name your-container-name your-dockerhub-username/your-image-name:v1
```
This will:
- Run the container in detached mode (-d)
- Map port 4000 of the container to port 4000 on the host (-p 4000:4000)

**3. Update and Rebuild the Docker Image(optional)**
If you make changes to your application and want to update the image, follow these steps:
 * **3.1. Make changes to your code.**
  ```bash
  docker build -t your-image-name .
  ```
 * **3.2. Tag the updated image:**
  ```bash
  docker tag your-image-name your-dockerhub-username/your-image-name:v2
  ```
 * **3.3. Push the updated image:**
  ```bash
  docker push your-dockerhub-username/your-image-name:v2
  ```
## Summary of Commands
```bash
# Build the Docker image
docker build -t your-image-name .

# Tag the Docker image
docker tag your-image-name your-dockerhub-username/your-image-name:v1

# Log in to Docker Hub
docker login

# Push the image to Docker Hub
docker push your-dockerhub-username/your-image-name:v1

# Pull the image from Docker Hub
docker pull your-dockerhub-username/your-image-name:v1

# Run the Docker container
docker run -d -p 4000:4000 --name your-container-name your-dockerhub-username/your-image-name:v1

# Rebuild the image after changes
docker build -t your-image-name .

# Remove a Docker container
docker stop your-container-name
docker rm your-container-name

# Remove a Docker image
docker rmi your-image-name:v1
```
---

### Resources
https://docs.digitalocean.com/products/app-platform/how-to/deploy-from-container-images/
https://devcenter.heroku.com/articles/container-registry-and-runtime
https://docs.render.com/deploy-an-image


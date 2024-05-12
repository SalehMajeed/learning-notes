# Docker Image

# Docker Image and Dockerfile Guide

## Introduction to Docker Images

Docker images are fundamental to Docker, encapsulating applications, dependencies, and runtime environments. Understanding how to work with Docker images is crucial for building and deploying containerized applications.

## Docker Image Commands

### 1. **`docker build Dockerfile-path`**

- Builds a Docker image using the specified Dockerfile.
- Example:
    
    ```bash
    docker build ./path/to/Dockerfile
    
    ```
    

### 2. **`docker build -t docker-id/tag-name:version Dockerfile-path`**

- Builds a Docker image with a specified tag and version.
- Example:
    
    ```bash
    docker build -t myusername/myapp:1.0 ./path/to/Dockerfile
    
    ```
    

### 3. **`docker commit -c 'CMD ["your-command"]' docker-id`**

- Creates a new image from a container and sets the default command.
- Example:
    
    ```bash
    docker commit -c 'CMD ["nginx"]' abc123
    
    ```
    

## Dockerfile Explanation and Example

### Dockerfile Overview

A Dockerfile is a script that defines the steps to create a Docker image. It includes instructions for the base image, setting the working directory, copying files, installing dependencies, exposing ports, and defining the default command.

### Example Dockerfile for Node.js Application

```
# Use an official Node.js runtime as a base image
FROM node:14

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the application code to the working directory
COPY . .

# Expose port 3000
EXPOSE 3000

# Define the command to run the application
CMD ["npm", "start"]
```

### **Building the Docker Image**

To build an image from the Dockerfile, use the following command:

```bash
docker build -t mynodeapp:1.0 .
```

This command builds an image with the tag **`mynodeapp:1.0`** from the current directory (**`.`**) containing the Dockerfile.

Now you have a basic understanding of Dockerfiles, Docker images, and how to create and customize them for your applications.
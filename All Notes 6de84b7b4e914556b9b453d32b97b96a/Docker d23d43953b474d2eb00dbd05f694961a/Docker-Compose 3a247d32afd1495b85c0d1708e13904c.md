# Docker-Compose

## **Introduction to Docker Compose**

Docker Compose is a tool for defining and managing multi-container Docker applications. It allows you to describe all the services, networks, and volumes for an application in a single YAML file, making it easier to manage complex setups and ensuring consistency across different environments.

## **Key Concepts**

### **1. Services**

- Each containerized application component is defined as a service.
- Examples include a web server, a database, or any other application component.

### **2. Volumes**

- Shared storage spaces that can be mounted into containers.
- Useful for persisting data or sharing files between containers.

### **3. Networks**

- Containers within the same Docker Compose application can communicate with each other through defined networks.
- Networks isolate and manage the communication between services.

## **Docker Compose File (docker-compose.yml)**

A Docker Compose file defines the structure of your Docker application, specifying services, networks, and volumes.

### **Example docker-compose.yml**

```yaml
yamlCopy code
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: example
  volumes:
    data_volume:

```

In this example:

- A web service is defined using the latest Nginx image, exposing port 8080.
- A database service uses the latest MySQL image, with a specified root password.
- A volume named **`data_volume`** is created for persistent data storage.

## **Common Docker Compose Commands**

### **1. `docker-compose up`**

- Builds and starts the services defined in the docker-compose.yml file.

### **2. `docker-compose up --build`**

- Builds and starts the services, ensuring a fresh build of images.

### 3**. `docker-compose down`**

- Stops and removes the containers, networks, and volumes defined in the docker-compose.yml file.

### 4**. `docker-compose ps`**

- Lists the status of services in the Docker Compose setup.

### 5**. `docker-compose logs`**

- Displays log output from services.

### 6**. `docker-compose exec <service-name> <command>`**

- Executes a command in a running service container.

### 7**. `docker-compose build`**

- Builds or rebuilds services.

### 8**. `docker-compose down -v`**

- Stops and removes containers, networks, and volumes, including data volumes.

Docker Compose simplifies the process of managing multi-container applications, providing a declarative way to define, orchestrate, and scale your Dockerized services.

### **Restart Policies in Docker Compose**

Restart policies define the conditions under which Docker Compose should restart containers that have exited. They are specified within the **`docker-compose.yml`** file for each service.

### 1. **`no`**

- **Description:** This is the default restart policy.
- **Behavior:**
    - Containers will not be automatically restarted if they exit.
- **Usage:**
    
    ```yaml
    yamlCopy code
    services:
      web:
        restart: no
    
    ```
    

### 2. **`always`**

- **Description:**
    - Always restart the container, regardless of the exit status.
- **Behavior:**
    - Docker Compose will restart the container indefinitely.
- **Usage:**
    
    ```yaml
    yamlCopy code
    services:
      web:
        restart: always
    
    ```
    

### 3. **`on-failure`**

- **Description:**
    - Restart the container only if it exits with a non-zero status.
- **Behavior:**
    - Docker Compose will restart the container if it exits with a non-zero status code.
- **Usage:**
    
    ```yaml
    yamlCopy code
    services:
      web:
        restart: on-failure
    
    ```
    

### 4. **`unless-stopped`**

- **Description:**
    - Always restart the container unless explicitly stopped by the user.
- **Behavior:**
    - Docker Compose will restart the container indefinitely, except when manually stopped.
- **Usage:**
    
    ```yaml
    yamlCopy code
    services:
      web:
        restart: unless-stopped
    
    ```
    

### **Example Usage in Docker Compose File**

```yaml
yamlCopy code
version: '3'
services:
  web:
    image: nginx:latest
    restart: always
    ports:
      - "80:80"

```

In this example, the **`web`** service uses the **`always`** restart policy. This means that the Nginx container will be automatically restarted by Docker Compose whenever it exits, ensuring the service is always running.

Choose the appropriate restart policy based on the requirements of your application and how you want to handle container restarts in different scenarios.

[Docker-compose file](Docker-Compose%203a247d32afd1495b85c0d1708e13904c/Docker-compose%20file%206cdd9fa76fbb435db7301fa3422b7466.md)
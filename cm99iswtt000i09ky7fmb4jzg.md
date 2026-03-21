---
title: "Understanding Docker Compose and How It Differs from Docker"
seoTitle: "Understanding Docker Compose and How It Differs from Docker"
seoDescription: "Understanding Docker Compose and How It Differs from Docker & how to use them in your full stack application"
datePublished: 2025-04-09T06:00:28.721Z
cuid: cm99iswtt000i09ky7fmb4jzg
slug: docker-compose-vs-docker
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/HSACbYjZsqQ/upload/7f9676c3821cab15136b58df0636c889.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1743812550884/b7a35043-b8c1-49ad-9ae9-79dbbd0ec6aa.png
tags: docker, docker-compose, docker-images

---


Docker is a powerful tool for containerizing applications, allowing developers to package software and its dependencies into a lightweight, portable container. While Docker focuses on managing individual containers, Docker Compose provides an efficient way to manage multi-container applications.

## What is Docker Compose?

Docker Compose is a tool for defining and running multi-container Docker applications. With a single YAML configuration file (`docker-compose.yml`), you can:

- Define multiple services (containers) and their configurations.
- Specify networks and volumes to enable communication between services.
- Start, stop, and manage all containers with a single command.

### Key Differences Between Docker and Docker Compose

| **Feature**              | **Docker**                                         | **Docker Compose**                                    |
|--------------------------|---------------------------------------------------|-----------------------------------------------------|
| **Purpose**              | Manages single containers.                        | Orchestrates multi-container applications.          |
| **Configuration**        | Requires separate commands for each container.    | Uses a single `docker-compose.yml` file for setup. |
| **Command Simplification** | Involves multiple `docker` commands.              | Simplifies with `docker-compose up` and `down`.     |
| **Networking**           | Requires manual linking of containers.            | Automatically sets up a shared network.             |

### When to Use Docker Compose

- **Multi-Service Applications**: Applications requiring multiple services, such as a database and API.
- **Development Environments**: Simulating production setups locally.
- **Rapid Deployment**: Starting all services with a single command.

## Building a Multi-Container Application with Docker Compose

Let's create a setup where:

1. A Node.js server communicates with a MySQL database.
2. phpMyAdmin is used to manage the database visually.
3. A React.js front-end interacts with the Node.js server.

### Directory Structure

```plaintext
project/
|-- backend/       # Node.js server code
|-- frontend/      # React.js app
|-- docker-compose.yml
```

### Step 1: Write the `docker-compose.yml` File

Create a `docker-compose.yml` file in the root directory:

```yaml
version: '3.8'
services:
  backend:
    build: ./backend
    ports:
      - "5000:5000"
    environment:
      - DB_HOST=mysql
      - DB_USER=root
      - DB_PASSWORD=root
      - DB_NAME=mydb
    depends_on:
      - mysql

  mysql:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: mydb
    ports:
      - "3306:3306"
    volumes:
      - db_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - "8080:80"
    environment:
      - PMA_HOST=mysql
      - MYSQL_ROOT_PASSWORD=root

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    depends_on:
      - backend

volumes:
  db_data:
```

### Step 2: Backend (Node.js Server)

1. In the `backend/` directory, create a `Dockerfile`:

    ```dockerfile
    FROM node:16-alpine

    WORKDIR /app

    COPY package*.json ./

    RUN npm install

    COPY . .

    EXPOSE 5000

    CMD ["npm", "start"]
    ```

2. Add your Node.js server code in this folder. Ensure the database connection uses environment variables like `DB_HOST`, `DB_USER`, etc.

### Step 3: Database (MySQL) and phpMyAdmin

No additional files are needed for these services since they use pre-built images.

### Step 4: Frontend (React.js App)

1. In the `frontend/` directory, create a `Dockerfile`:

    ```dockerfile
    FROM node:16-alpine

    WORKDIR /app

    COPY package*.json ./

    RUN npm install

    COPY . .

    EXPOSE 3000

    CMD ["npm", "start"]
    ```

2. Place your React.js app code here. Ensure API requests point to the `backend` service (e.g., `http://backend:5000`).

### Step 5: Running the Application

1. **Start the Services**:
   Run the following command in the project directory:

   ```bash
   docker-compose up --build
   ```

2. **Access the Services**:
   - Node.js backend: `http://localhost:5000`
   - React.js frontend: `http://localhost:3000`
   - phpMyAdmin: `http://localhost:8080` (Login with `root`/`root` for credentials)

3. **Stop the Services**:
   Use:

   ```bash
   docker-compose down
   ```

## Conclusion

By using Docker Compose, we’ve created a robust environment to develop and manage a multi-service application seamlessly. The simplicity of managing interconnected services makes Docker Compose an essential tool for modern developers. As you continue experimenting, you’ll find ways to optimize your workflow and integrate Docker Compose into larger projects.


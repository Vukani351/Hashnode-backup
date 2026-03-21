---
title: "Understanding Docker and Docker Compose as a Junior Front-End Developer"
seoTitle: "Using docker for front end project"
seoDescription: "Here is a process to use to run vuejs project on docker. This helped me with my journey into learning docker."
datePublished: 2025-04-07T06:00:17.646Z
cuid: cm96nwyy6000p09js23h7cq1d
slug: understanding-docker-and-docker-compose-as-a-junior-front-end-developer
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/jOqJbvo1P9g/upload/5564e5a6ac83456bf6993b5f5e399f8d.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1743812243840/72cda019-b20e-4b3b-adc5-4805a1e4544a.png
tags: docker, deployment, vuejs, render

---


As a junior front-end developer, my journey into Docker started as I sought to grow my skills and tackle more complex projects. Docker might seem like a tool primarily for back-end developers or DevOps, but its benefits for front-end workflows have proven invaluable. In this article, I’ll share:

1. why I began learning Docker.
2. how it fits into the development process.
3. practical steps to get started using Docker for your own front-end projects.

## Why I Started Learning Docker

When starting as a front-end developer, my primary focus was mastering frameworks like React or  Vue.js & tools like Render to deploy single applications. As my projects grew in complexity and I began collaborating more at work, I saw a need to manage multiple interconnected applications effectively. Docker stood out as a solution to package & deploy these applications consistently.

Docker allows you to:

- **Standardize environments**: No more “it works on my machine” issues.
- **Simplify deployments**: Package applications with their dependencies into lightweight containers.
- **Enhance collaboration**: Share the same development setup with your team.

### When Docker is Used in the Development Process

Docker shines in scenarios like:

- Running isolated development environments.
- Deploying microservices.
- Testing applications in production-like conditions.
- Simplifying CI/CD pipelines.

## Seeing the Need for Docker

Initially, tools like Render made deploying single applications straightforward. However, as I began working on projects with multiple services—for instance, a front-end client, a back-end API, and a database—the limitations of traditional deployment methods became evident. Managing these services manually or relying on third-party tools was cumbersome.

At work, Docker started becoming useful for:

- Running multiple applications locally without conflicts.
- Standardizing the development environment across team members.
- Simplifying the deployment process for multi-service applications.

## Installing Docker Desktop Locally

Getting started with Docker requires installing Docker Desktop on your machine. Here’s how you can do it:

1. **Download Docker Desktop**:
   - Visit the [Docker Desktop download page](https://www.docker.com/products/docker-desktop/).
   - Select the version suitable for your operating system (Windows, macOS, or Linux).

2. **Install Docker Desktop**:
   - Follow the installation instructions for your OS.
   - On Windows, ensure that WSL2 is enabled for better performance.

3. **Verify the Installation**:
   - Open a terminal and run `docker --version`.
   - You should see the installed Docker version.

4. **Start Docker Desktop**:
   - Launch Docker Desktop and make sure it’s running in the background.

## Running a Vue.js Project on Docker

Let’s walk through running a Vue.js project in a Docker container:

1. **Create a Dockerfile** in your project directory. This file defines the steps to build your container:

    ```dockerfile
    # Use the official Node.js image as a base
    FROM node:16-alpine

    # Set the working directory in the container
    WORKDIR /app

    # Copy package.json and package-lock.json
    COPY package*.json ./

    # Install dependencies
    RUN npm install

    # Copy the rest of the application’s code
    COPY . .

    # Expose the port your app runs on
    EXPOSE 8080

    # Define the command to start the app
    CMD ["npm", "run", "serve"]
    ```

2. **Create a `docker-compose.yml` file** for managing multi-container applications (optional):

    ```yaml
    version: '3.8'
    services:
      vuejs-app:
        build: .
        ports:
          - "8080:8080"
        volumes:
          - .:/app
          - /app/node_modules
        command: npm run serve
    ```

3. **Build and Run the Docker Container**:
   - Build the image: `docker build -t vuejs-app .`
   - Run the container: `docker run -p 8080:8080 vuejs-app`

4. **Access Your Application**:
   - Open your browser and navigate to `http://localhost:8080`.

For a detailed guide on creating a Dockerfile, check out [Docker’s official documentation](https://docs.docker.com/engine/reference/builder/).

## Growing Efficiency with Docker

Learning Docker has been a game-changer for me. It’s helped me:

- Run personal projects locally with consistent environments.
- Experiment with deploying multi-service applications.
- Collaborate more effectively with team members by sharing Docker configurations.

As I continue to grow my Docker skills, I’ve realized that the key is to start small and gradually build on your knowledge. Whether you’re deploying a simple Vue.js app or managing a complex project, Docker is an invaluable tool for any developer.

I hope this article inspires you to take the first steps into the world of Docker. Happy coding!


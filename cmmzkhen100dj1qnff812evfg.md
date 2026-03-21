---
title: "How to Run a Docker Project on AWS EC2:"
seoTitle: "How to run a docker project on AWS ec2"
seoDescription: "This is How to run a docker project on AWS EC2 instance. Step by step process to follow"
datePublished: 2026-03-21T00:05:42.112Z
cuid: cmmzkhen100dj1qnff812evfg
slug: docker-project-on-ec2
cover: https://cdn.hashnode.com/uploads/covers/624c31412b09bb392ea5cf5e/7fd4e268-435b-4e04-9a68-060ed832817b.jpg
ogImage: https://cdn.hashnode.com/uploads/og-images/624c31412b09bb392ea5cf5e/a32439ed-042f-43ad-b16b-9455e4a8f51e.jpg
tags: aws, docker-images, ec2-instance

---

Deploying and running a Docker project on AWS EC2 can seem challenging, especially when your local development environment only contains a `Dockerfile` and you need to get it up and running in a cloud-based setup. In this article, I’ll walk you through the process of preparing your AWS EC2 instance, deploying your Docker project, making it accessible publicly, and finally, testing the setup.

* * *

### **Context: The Challenge**

I faced a situation where I had cloned a project from GitHub onto an AWS EC2 instance. The project only contained a `Dockerfile`, and I needed to get the image built, run it as a container, and make it accessible via HTTP. The goal was to have a web application running on the instance that could be accessed publicly through a domain or the instance's IP address.

### **Solution Steps: Setting Up Docker on AWS EC2 and Running the Project**

#### **Step 1: Prepare the EC2 Instance**

First, I spun up an AWS EC2 instance, making sure that Docker was installed:

*   **Launch the EC2 Instance:**
    
    *   I created an Amazon Linux 2 instance (or you can choose Ubuntu depending on preference).
        
    *   I assigned a security group that allowed HTTP traffic (port `80`) from the internet.
        
*   **Connect to the EC2 Instance:**
    
    ```bash
    ssh -i "your-key.pem" ec2-user@your-ec2-instance-ip
    ```
    
*   **Install Docker:**
    
    ```bash
    sudo yum install docker -y   # For Amazon Linux
    sudo apt install docker.io -y  # For Ubuntu
    ```
    
*   **Start Docker:**
    
    ```bash
    sudo systemctl start docker
    sudo systemctl enable docker
    ```
    
*   **Verify Docker Installation:**
    
    ```bash
    docker --version
    ```
    

#### **Step 2: Cloning the Repository**

I cloned the project containing the `Dockerfile` onto the EC2 instance:

```bash
git clone https://github.com/your-repo.git
```

*   **Navigate to the Project Directory:**
    
    ```bash
    cd /home/ec2-user/your-project
    ```
    

#### **Step 3: Build the Docker Image**

Next, I built the Docker image from the `Dockerfile`:

```bash
sudo docker build -t your-project-image .
```

*   `-t` tags the Docker image as `your-project-image`.
    
*   `.` indicates the current directory (where `Dockerfile` is located).
    

#### **Step 4: Run the Docker Container**

Once the image was built, I ran it as a container:

```bash
sudo docker run -d -p 80:80 your-project-image
```

*   `-d` runs the container in detached mode.
    
*   `-p 80:80` maps port `80` on the host to port `80` inside the container.
    

#### **Step 5: Verify the Container is Running**

To confirm the container is running:

```bash
sudo docker ps
```

This will show all the currently running Docker containers.

#### **Step 6: Access the Application**

I accessed my web application using the public IP of the EC2 instance:

```bash
http://your-ec2-instance-ip
```

At this point, I expected my application to be accessible publicly, provided the EC2 security group allowed traffic on port `80`.

* * *

### **Step 7: (Optional) Using Elastic IP**

Since public IPs can change when restarting EC2 instances, I allocated an Elastic IP:

```bash
aws ec2 allocate-address
```

Once the IP was allocated, I associated it with my EC2 instance.

* * *

### **Step 8: (Optional) Configure a Domain Name**

To make the application more accessible, I configured Route 53 (AWS’s DNS service) to point my domain to the Elastic IP:

```bash
# Go to Route 53 in AWS and create a new hosted zone.
```

Once set, my domain (`your-domain.com`) would resolve to the EC2 instance's Elastic IP.

* * *

### **Step 9: Testing the Application**

To ensure everything is working properly:

*   **Check Container Logs:**
    
    ```bash
    sudo docker logs <container_id_or_name>
    ```
    
    This shows what’s going on inside the container, helping diagnose potential issues.
    
*   **Validate the Web Application:**
    
    *   Visit `http://your-ec2-instance-ip` or your domain in a browser.
        
    *   You should see your web application running.
        

* * *

### **Conclusion**

Running Docker on AWS EC2, especially from a `Dockerfile`, involves a few key steps: installing Docker, building the Docker image, running the container, and making it publicly accessible. Once everything is configured properly, you can manage your Dockerized applications with ease.

This process helped me set up a web application on AWS EC2, accessible via HTTP, with room to expand if I wanted to add more features like scaling or monitoring.
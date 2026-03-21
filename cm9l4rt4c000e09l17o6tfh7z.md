---
title: "Understanding Github Actions"
seoTitle: "introduction to github actions"
seoDescription: "Learn how to use github actions, understand how it works & automating AWS deploys triggered by git push."
datePublished: 2025-04-17T09:00:56.748Z
cuid: cm9l4rt4c000e09l17o6tfh7z
slug: understanding-github-actions
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wX2L8L-fGeA/upload/0c61765df80bda8034e5a3e39feb4737.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1744829679919/ee6198ad-97f3-4ca6-80a7-86b0de0c34ab.avif
tags: aws, github, automation, github-actions, github-actions-1, ec2-instance

---

To learn GitHub Actions and set up a workflow to build and deploy your app on AWS EC2, you'll need to understand the following fundamentals:

1. **GitHub Actions Basics**:
   - **Workflow**: A YAML file that defines the automation process.
   - **Job**: A set of steps that execute on the same runner.
   - **Step**: An individual task within a job.
   - **Runner**: The server that runs your workflows.

2. **YAML Syntax**:
   - Understand the structure and syntax of YAML files, as GitHub Actions workflows are defined in YAML.

3. **Triggers**:
   - **on**: Events that trigger the workflow, such as `push`, `pull_request`, `schedule`, etc.

4. **Jobs**:
   - How to define and configure jobs within a workflow.
   - Understanding job dependencies with `needs`.

5. **Steps**:
   - How to define steps within jobs.
   - Running shell commands or using pre-built GitHub Actions.

6. **GitHub Actions Marketplace**:
   - Using pre-built actions from the GitHub Actions Marketplace.

7. **Secrets and Environment Variables**:
   - Storing sensitive information like AWS credentials in GitHub Secrets.
   - Using environment variables in workflows.

8. **AWS CLI and EC2**:
   - Basic knowledge of AWS CLI commands.
   - How to set up and configure an EC2 instance.
   - Deploying applications to EC2 using GitHub Actions.

### Example GitHub Actions Workflow for Deploying to AWS EC2

Here's an example workflow that builds and deploys a Node.js application to an AWS EC2 instance, with comments explaining each part:

```yaml
# Name of the workflow
name: CI/CD Pipeline

# Trigger the workflow on push events to the main branch
on:
  push:
    branches:
      - main  # Branch name that triggers the workflow

# Define the jobs in the workflow
jobs:
  # Build job
  build:
    # Use the latest version of Ubuntu as the runner
    runs-on: ubuntu-latest

    # Define the steps in the build job
    steps:
      # Step to checkout the repository code
      - name: Checkout code
        uses: actions/checkout@v2

      # Step to set up Node.js environment
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'  # Specify the Node.js version

      # Step to install Node.js dependencies
      - name: Install dependencies
        run: npm install

      # Step to run tests
      - name: Run tests
        run: npm test

      # Step to build the application
      - name: Build the app
        run: npm run build

  # Deploy job
  deploy:
    # Use the latest version of Ubuntu as the runner
    runs-on: ubuntu-latest
    # This job depends on the successful completion of the build job
    needs: build

    # Define the steps in the deploy job
    steps:
      # Step to checkout the repository code
      - name: Checkout code
        uses: actions/checkout@v2

      # Step to set up SSH agent
      - name: Setup SSH
        uses: webfactory/ssh-agent@v0.5.3
        with:
          ssh-private-key: ${{ secrets.AWS_SSH_KEY }}  # Use the SSH private key stored in GitHub Secrets

      # Step to deploy the built application to the EC2 instance
      - name: Deploy to EC2
        run: |
          # Securely copy the build directory to the EC2 instance
          scp -r ./build ec2-user@${{ secrets.EC2_HOST }}:/var/www/myapp
          # Restart the application on the EC2 instance
          ssh ec2-user@${{ secrets.EC2_HOST }} 'sudo systemctl restart myapp'
```

### Steps to Follow

1. **Create a GitHub Repository**: Create a new repository or use an existing one.
2. **Create `.github/workflows` Directory**: In your repository, create a directory named `.github/workflows`.
3. **Create a Workflow File**: Inside the `.github/workflows` directory, create a YAML file (e.g., `ci-cd.yml`) with the example content above.
4. **Add Secrets**:
   - Go to your repository settings, then "Secrets and variables" > "Actions".
   - Add secrets such as `AWS_SSH_KEY` and `EC2_HOST` with your EC2 instance details and SSH key.
5. **Push Changes**: Commit and push the changes to trigger the workflow.

By understanding these concepts and following the example, you'll be able to create and configure GitHub Actions workflows to build and deploy your front-end application to AWS EC2.
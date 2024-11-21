# Web Application Deployment using Docker, Jenkins, Ansible, and AWS EC2

This project demonstrates the deployment of a web application using DevOps tools like Docker, Jenkins, and Ansible, hosted on AWS EC2 instances. The setup involves:

- **Docker**: To containerize the application and manage containers.
- **Jenkins**: For setting up a CI/CD pipeline with automated builds and deployments.
- **Ansible**: To orchestrate and automate application deployment using playbooks.
- **AWS EC2 Instances**: To host the Docker and Jenkins environments with secure SSH connections.

## Features
- Automated CI/CD pipeline with Jenkins.
- Dynamic container deployment using Ansible.
- Two-way SSH connection between instances for seamless communication.
- Hosting a web application using Docker containers.

## Project Workflow
1. Code changes in the GitHub repository trigger a Webhook to Jenkins.
2. Jenkins executes a CI/CD pipeline that builds the Docker image and deploys containers.
3. Ansible playbooks manage container creation, stopping, and removal on the Docker instance.
4. The web application is hosted on the Docker instance and accessible via the provided public IP.
## Pipeline Configuration
   The **Execute Shell** step in the Jenkins pipeline includes the following commands:
   ```bash
   scp -r /var/lib/jenkins/workspace/ansible-jenkins-pipeline/* root@172.31.41.15:/project (docker private ip)
   ansible-playbook /var/lib/jenkins/playbooks/deployment.yaml
   ```
## Prerequisites
- AWS account with two Ubuntu 24.04 LTS EC2 instances (T2.micro, 10 GB storage).
- Install and configure Docker in one instance and Jenkins, and Ansible in the other instance.
- GitHub repository containing application code and Dockerfile.

## Usage
1. Clone the repository.
   ```bash
   git clone https://github.com/koushik12098/guarder.git
2. Configure Jenkins with the pipeline and set up Webhook integration with GitHub.
3. Run the Ansible playbook to deploy the application.
   ```bash
   ansible-playbook /path/to/deployment.yaml
4. Access the application using the public IP of the Docker instance.


# Install Jenkins in a Docker Container on DigitalOcean Virtual Machine (aka "Droplet")

## Overview
This repository documents the steps to install and run Jenkins inside a Docker container on a DigitalOcean Virtual Machine ("droplet"). Jenkins is an open-source automation server widely used for CI/CD pipelines.

## Why run Jenkins in a Docker container instead of installing it directly on the Droplet OS?
* Isolation & Portability
  - Jenkins and its dependencies live inside the container, avoiding conflicts with host packages.
  - The same image works across different VMs/clouds—build once, run anywhere.
* Simplified Installation & Upgrades
  - No need to install Java or configure system services on the droplet.
  - Upgrading Jenkins is as simple as pulling a new Docker image and restarting the container.
* Consistency Across Environments
  - The same Docker image can be used in development, staging, and production, ensuring consistent behavior.
* Easy Backup & Restore
  - Jenkins data is stored in a Docker volume, making backups straightforward.
  - You can quickly restore by mounting the same volume to a new container.

## Prerequisites
* A DigitalOcean account and a provisioned droplet (Ubuntu recommended).
* SSH access to the droplet.
* Docker and Docker Compose installed.
* Basic knowledge of Linux commands.

## Steps
1. Provision a DigitalOcean Droplet
   - Create a Droplet
   - Configure SSH keys for secure access
2. Install Docker
   - Run the following commands on your droplet
3. Pull latest Jenkins Docker Image from DockerHub
4. Run Jenkins Container
5. Access Jenkins
   - Open your favorite browser and go to: `http://<your-droplet-ip>:8080/`
   - Retrieve the initial admin password `docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword`
6. Configure Jenkins
   - Install recommended plugins
   - Create your first admin user
7. Start building pipelines!
   





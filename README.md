# Install Jenkins in a Docker Container on DigitalOcean Virtual Machine (aka "Droplet")

## Overview
This repository documents the steps to install and run Jenkins inside a Docker container on a DigitalOcean Virtual Machine ("droplet"). Jenkins is an open-source automation server widely used for CI/CD pipelines.

## Why run Jenkins in a Docker container instead of installing it directly on the Droplet OS?
* **Isolation & Portability**
  - Jenkins and its dependencies live inside the container, avoiding conflicts with host packages.
  - The same image works across different VMs/clouds—build once, run anywhere.
* **Simplified Installation & Upgrades**
  - No need to install Java or configure system services on the droplet.
  - Upgrading Jenkins is as simple as pulling a new Docker image and restarting the container.
* **Consistency Across Environments**
  - The same Docker image can be used in development, staging, and production, ensuring consistent behavior.
* **Easy Backup & Restore**
  - Jenkins data is stored in a Docker volume, making backups straightforward.
  - You can quickly restore by mounting the same volume to a new container.
* **Faster Recovery & Scaling**
  - If Jenkins crashes, you can redeploy the container in seconds.
  - Supports horizontal scaling with container orchestration tools like Kubernetes.
* **Cleaner Host System**
  - Keeps the VM clean—no extra packages or dependencies installed on the OS.
  - Reduces risk of breaking the system when upgrading Jenkins or its dependencies.

## Prerequisites
Before you being, make sure you have:
* A DigitalOcean account (or any cloud provider).
* Basic knowledge of Linux commands and SSH.
* A local machine with SSH client installed (to connect to the droplet).

## Steps
1. Provision a DigitalOcean Droplet
   - Create a Droplet
     - **Datacenter** - Choose the closest datacenter to you
     - **OS** - Select *Ubuntu* as the OS with the latest version.
     - **Droplet Type** - Select *Shared CPU - Basic* option.
     - **CPU options** - Select the *2CPUs - 4GB RAM - 80GB* which should be sufficient enough to run Jenkins Docker container.
   - Configure SSH keys for secure access
     - You can follow the instructions provided by DigitalOcean to generate the public and private SSH keys.
   - Create and attach firewall to new droplet
     - **Inbound Rules**
       - Restrict port 22 (SSH) and 8080 (Jenkins) to trusted client machine IPs.       
2. Install Docker
   - Run the following commands on your droplet
3. Pull latest Jenkins Docker Image from DockerHub
4. Run Jenkins Container
5. Access Jenkins
   - Open your favorite browser and go to: ```http://<your-droplet-ip>:8080/```
   - Retrieve the initial admin password ```docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword```
6. Configure Jenkins
   - Install recommended plugins
   - Create your first admin user
7. Start building pipelines!
   





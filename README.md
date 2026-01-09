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
   - Create a new network firewall rule for the droplet.
     - Assign any name for the firewall such as "jenkins-fw".
     - **Inbound Rules**
       - Restrict port 22 (SSH) and 8080 (Jenkins) to trusted client machine IPs.
     - Attach the droplet to the new firewall.
       
2. Launch the droplet and connect to it using its public IPv4 address:
  ```
  ssh root@<your-droplet-public-ipv4>
  ```
  - Note: You won’t be prompted for a password if:
    - SSH keys were correctly configured during droplet creation.
    - The public key was added to the droplet.
    - The corresponding private key is available on your local machine.
      
3. Install Docker and Docker Compose
   - Run the following commands on your droplet
     ```
     apt update
     apt install docker
     apt install docker-compose
     
     ```
     
4. Pull latest Jenkins Docker Image from DockerHub

5. Run Jenkins Container

6. Access Jenkins
   - Open your favorite browser and go to:
     ```
     http://<your-droplet-public-ipv4>:8080/
     ```
   - Retrieve the initial admin password
     ```
     docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
     ```

7. Configure Jenkins
   - Install recommended plugins
   - Create your first admin user

8. Start building pipelines!
   





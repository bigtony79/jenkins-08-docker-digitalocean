# Install Jenkins in a Docker Container on DigitalOcean Virtual Machine (aka "Droplet")
## Overview
This repository documents the steps to install and run Jenkins inside a Docker container on a DigitalOcean Virtual Machine ("droplet"). Jenkins is an open-source automation server widely used for CI/CD pipelines.

## Prerequisites
* A DigitalOcean account and a provisioned VM (Ubuntu recommended).
* SSH access to the VM.
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
   - Open your favorite browser and go to: 'http://<your-droplet-ip>:8080/'
   





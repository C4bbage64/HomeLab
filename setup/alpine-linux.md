# AlpineLinux-Docker Setup Guide

## Overview
This document outlines the setup and configuration of the AlpineLinux-Docker VM, which will serve as a lightweight Docker host in the homelab.

## Prerequisites
- Alpine Linux ISO image.
- VirtualBox or another virtualization software.

## Installation Steps
1. **Create a New VM**:
   - Name: `AlpineLinux-Docker`
   - Type: Linux
   - Version: Other Linux (64-bit)
   - Allocate at least 512MB of RAM and 5GB of storage.

2. **Install Alpine Linux**:
   - Attach the Alpine Linux ISO to the VM.
   - Start the VM and log in as `root`.
   - Run the setup script:
     ```bash
     setup-alpine
     ```
   - Follow the prompts to configure the hostname, networking, and root password.

3. **Post-Installation Configuration**:
   - Update the package repository:
     ```bash
     apk update
     ```
   - Install Docker:
     ```bash
     apk add docker
     rc-update add docker boot
     service docker start
     ```
   - Install `sudo` if necessary:
     ```bash
     apk add sudo
     ```
   - Add your user to the Docker group:
     ```bash
     adduser username docker
     ```

4. **Networking Configuration**:
   - Use a Bridged Adapter for networking.
   - Verify connectivity with other VMs using `ping`.

## Usage
- Host and run Docker containers with minimal resource overhead.

## Troubleshooting
- Check Docker service status if issues arise:
     ```bash
     service docker status
     ```

## Future Enhancements
- Set up Docker Compose or swarm mode for orchestrating multiple containers.

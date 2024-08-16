# RockyLinux-DB Setup Guide

## Overview
This document outlines the setup and configuration of the RockyLinux-DB VM, which will serve as the Database Server in the homelab.

## Prerequisites
- Rocky Linux ISO image.
- VirtualBox or another virtualization software.

## Installation Steps
1. **Create a New VM**:
   - Name: `RockyLinux-DB`
   - Type: Linux
   - Version: Red Hat (64-bit)
   - Allocate at least 2GB of RAM and 30GB of storage.

2. **Install Rocky Linux**:
   - Attach the Rocky Linux ISO to the VM.
   - Start the VM and follow the installation wizard.
   - Set up the server with a hostname (e.g., `rocky-db`) and user credentials.

3. **Post-Installation Configuration**:
   - Update the system:
     ```bash
     sudo dnf update -y
     ```
   - Install OpenSSH Server:
     ```bash
     sudo dnf install -y openssh-server
     sudo systemctl enable sshd
     sudo systemctl start sshd
     ```
   - Install a Database Server (e.g., PostgreSQL):
     ```bash
     sudo dnf install -y postgresql-server postgresql-contrib
     sudo postgresql-setup --initdb
     sudo systemctl enable postgresql
     sudo systemctl start postgresql
     ```

4. **Networking Configuration**:
   - Use a Bridged Adapter for networking.
   - Verify connectivity with other VMs using `ping`.

## Usage
- Host and manage databases, interact with Kubernetes or client VMs for data storage.

## Troubleshooting
- Check PostgreSQL service status and logs if issues arise.

## Future Enhancements
- Set up database replication or clustering.

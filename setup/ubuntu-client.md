# Ubuntu-Client VM Setup Guide

## Overview
This document outlines the steps to set up the Ubuntu-Client VM, which will act as a client machine in the homelab environment.

## Prerequisites
- Download the Ubuntu Desktop ISO image.
- VirtualBox or any other virtualization software.

## Installation Steps
1. **Create a New VM**:
   - Name: `Ubuntu-Client`
   - Type: Linux
   - Version: Ubuntu (64-bit)
   - Allocate at least 2GB of RAM and 20GB of storage.

2. **Install Ubuntu Desktop**:
   - Attach the Ubuntu Desktop ISO to the VM.
   - Start the VM and follow the installation wizard.
   - Select the appropriate language, keyboard layout, and other preferences.
   - Install Ubuntu with default settings.

3. **Post-Installation Configuration**:
   - Update the system:
     ```bash
     sudo apt-get update && sudo apt-get upgrade -y
     ```
   - Install OpenSSH client (optional for SSH access to other servers):
     ```bash
     sudo apt-get install openssh-client
     ```

4. **Networking Configuration**:
   - Ensure the VM is connected to the correct network (e.g., Bridged Adapter) to communicate with other VMs.

## Usage
- This VM will be used to interact with the Kubernetes cluster, access the database on RockyLinux-DB, and run client-side applications.

## Troubleshooting
- If network issues arise, check the network settings in VirtualBox and ensure the correct adapter is selected.

## Future Enhancements
- Consider setting up a GUI-based management tool or installing additional client-side software as needed.

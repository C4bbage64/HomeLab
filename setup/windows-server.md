# WindowsServer-2022 Setup Guide

## Overview
This document outlines the setup and configuration of the WindowsServer-2022 VM, which will serve as the Windows-based Application Server in the homelab.

## Prerequisites
- Windows Server 2022 ISO image.
- VirtualBox or another virtualization software.

## Installation Steps
1. **Create a New VM**:
   - Name: `WindowsServer-2022`
   - Type: Microsoft Windows
   - Version: Windows 2022 (64-bit)
   - Allocate at least 4GB of RAM and 50GB of storage.

2. **Install Windows Server 2022**:
   - Attach the Windows Server 2022 ISO to the VM.
   - Start the VM and follow the installation wizard.
   - Choose the appropriate edition with GUI.
   - Set up the server with a hostname (e.g., `windows-server`) and administrator credentials.

3. **Post-Installation Configuration**:
   - Update the system and install Windows updates.
   - Install IIS for web services:
     - Open **Server Manager**.
     - Navigate to **Add Roles and Features**.
     - Select **Web Server (IIS)** and complete the installation.

4. **Networking Configuration**:
   - Use a Bridged Adapter for networking.
   - Verify connectivity with other VMs.

## Usage
- Host Windows-specific applications, manage Active Directory or IIS web services.

## Troubleshooting
- Check event logs and IIS configurations if issues arise.

## Future Enhancements
- Configure additional roles like DNS, DHCP, or Hyper-V.

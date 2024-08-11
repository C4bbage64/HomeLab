Homelab README
Overview
This homelab is set up to provide a hands-on learning environment for cloud computing, containerization, and infrastructure management. It consists of several virtual machines (VMs) configured to simulate a real-world cloud environment.

Architecture
VM 1: Ubuntu Server (Kubernetes Control Plane)

Role: Kubernetes Control Plane Node or Docker Host
Purpose: Manage Kubernetes clusters or run containerized applications.
VM 2: Rocky Linux (Database Server)

Role: Database Server (e.g., PostgreSQL, MySQL)
Purpose: Host databases and learn about data storage in the cloud.
VM 3: Windows Server 2022

Role: Windows-based Application Server
Purpose: Run Windows-specific applications, Active Directory, or IIS for web services.
VM 4: Alpine Linux (Docker Host)

Role: Lightweight Container Host
Purpose: Run Docker containers with minimal resource overhead.
VM 5: Client VM(s)

Role: Test access and interaction with the services provided by the server VMs.
Purpose: Simulate client access to the deployed services and applications.
Installation and Configuration
1. Ubuntu Server Setup
Install Kubernetes:

Follow the instructions to install Kubernetes and set up the control plane.
Install Docker (Optional):

apt-get update && apt-get install docker.io
Deploy Applications:

Create Kubernetes deployment and service files.
Deploy your applications using kubectl apply.
2. Rocky Linux Setup
Install and Configure Database:

Install PostgreSQL/MySQL.
Set up databases and users for application use.
Ensure Connectivity:

Verify that the database server is accessible from other VMs.
3. Windows Server 2022 Setup
Install and Configure Services:
Set up Active Directory, IIS, or other required services.
Configure user permissions and network settings.
4. Alpine Linux Setup
Install Docker:

apk update
apk add docker
Run Docker Containers:

Build and run Docker containers for lightweight application deployment.
5. Client VM Setup
Install Client Software:
Set up necessary software to interact with services running on the server VMs.
Ensure network connectivity between client and server VMs.
Testing and Verification
Application Testing:

Access applications through exposed services or IP addresses.
Verify functionality and connectivity.
Database Testing:

Ensure that the database server is properly integrated with deployed applications.
Service Verification:

Check the status and logs of services running on all VMs.
Troubleshooting
Check Logs:

Use kubectl logs, docker logs, or service-specific logs to diagnose issues.
Verify Connectivity:

Ensure network configurations and firewall rules are correctly set.
Reconfigure Services:

Edit configuration files or redeploy services as needed.
Additional Resources
Kubernetes Documentation
Docker Documentation
Alpine Linux Documentation
Rocky Linux Documentation
License
This project is licensed under the MIT License. See LICENSE for details.


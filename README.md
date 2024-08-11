# Homelab README

## Overview

This homelab is set up to provide a hands-on learning environment for cloud computing, containerization, and infrastructure management. It consists of several virtual machines (VMs) configured to simulate a real-world cloud environment.

## Architecture

- **VM 1: Ubuntu Server (Kubernetes Control Plane)**
  - **Role**: Kubernetes Control Plane Node or Docker Host
  - **Purpose**: Manage Kubernetes clusters or run containerized applications.

- **VM 2: Rocky Linux (Database Server)**
  - **Role**: Database Server (e.g., PostgreSQL, MySQL)
  - **Purpose**: Host databases and learn about data storage in the cloud.

- **VM 3: Windows Server 2022**
  - **Role**: Windows-based Application Server
  - **Purpose**: Run Windows-specific applications, Active Directory, or IIS for web services.

- **VM 4: Alpine Linux (Docker Host)**
  - **Role**: Lightweight Container Host
  - **Purpose**: Run Docker containers with minimal resource overhead.

- **VM 5: Client VM(s)**
  - **Role**: Test access and interaction with the services provided by the server VMs.
  - **Purpose**: Simulate client access to the deployed services and applications.

## Installation and Configuration

### 1. **Ubuntu Server Setup**

1. **Install Kubernetes**:
   - Follow the instructions to install Kubernetes and set up the control plane.

2. **Install Docker (Optional)**:
   - ```bash
     apt-get update && apt-get install docker.io
     ```

3. **Deploy Applications**:
   - Create Kubernetes deployment and service files.
   - Deploy your applications using:
     ```bash
     kubectl apply -f <deployment-file>.yaml
     ```

### 2. **Rocky Linux Setup**

1. **Install and Configure Database**:
   - Install PostgreSQL/MySQL:
     - ```bash
       apk add postgresql postgresql-contrib  # For PostgreSQL
       apk add mysql mysql-client            # For MySQL
       ```
   - Set up databases and users:
     ```bash
     psql -U postgres
     CREATE DATABASE student_db;
     CREATE USER student_user WITH ENCRYPTED PASSWORD 'your_password';
     GRANT ALL PRIVILEGES ON DATABASE student_db TO student_user;
     ```

2. **Ensure Connectivity**:
   - Verify that the database server is accessible from other VMs.

### 3. **Windows Server 2022 Setup**

1. **Install and Configure Services**:
   - Set up Active Directory, IIS, or other required services.
   - Configure user permissions and network settings.

### 4. **Alpine Linux Setup**

1. **Install Docker**:
   - ```bash
     apk update
     apk add docker
     ```

2. **Run Docker Containers**:
   - Build and run Docker containers for lightweight application deployment.

### 5. **Client VM Setup**

1. **Install Client Software**:
   - Set up necessary software to interact with services running on the server VMs.
   - Ensure network connectivity between client and server VMs.

## Testing and Verification

1. **Application Testing**:
   - Access applications through exposed services or IP addresses.
   - Verify functionality and connectivity.

2. **Database Testing**:
   - Ensure that the database server is properly integrated with deployed applications.

3. **Service Verification**:
   - Check the status and logs of services running on all VMs.

## Troubleshooting

1. **Check Logs**:
   - Use `kubectl logs`, `docker logs`, or service-specific logs to diagnose issues.

2. **Verify Connectivity**:
   - Ensure network configurations and firewall rules are correctly set.

3. **Reconfigure Services**:
   - Edit configuration files or redeploy services as needed.

## Additional Resources

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Docker Documentation](https://docs.docker.com/)
- [Alpine Linux Documentation](https://wiki.alpinelinux.org/)
- [Rocky Linux Documentation](https://docs.rockylinux.org/)

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

# UbuntuServer-K8s Setup Guide

## Overview
This document outlines the setup and configuration of the UbuntuServer-K8s VM. It will serve as the Kubernetes Control Plane Node or Docker Host in the homelab environment.

## Prerequisites
- Ubuntu Server ISO image.
- VirtualBox or another virtualization software.

## Installation Steps
1. **Create a New VM**:
   - Name: `UbuntuServer-K8s`
   - Type: Linux
   - Version: Ubuntu (64-bit)
   - Allocate at least 4GB of RAM and 40GB of storage.

2. **Install Ubuntu Server**:
   - Attach the Ubuntu Server ISO to the VM.
   - Start the VM and follow the installation wizard.
   - Choose "Minimal Installation" for a lightweight setup.
   - Set up the server with an appropriate hostname (e.g., `ubuntu-k8s`) and user credentials.

3. **Post-Installation Configuration**:
   - Update the system:
     ```bash
     sudo apt-get update && sudo apt-get upgrade -y
     ```
   - Install OpenSSH Server:
     ```bash
     sudo apt-get install openssh-server
     ```
   - Install Docker (if planning to use it):
     ```bash
     sudo apt-get install docker.io
     sudo systemctl enable docker
     sudo systemctl start docker
     ```
   - Install Kubernetes tools (Kubeadm, Kubelet, Kubectl):
     ```bash
     sudo apt-get update && sudo apt-get install -y apt-transport-https curl
     curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
     sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
     sudo apt-get update
     sudo apt-get install -y kubelet kubeadm kubectl
     sudo apt-mark hold kubelet kubeadm kubectl
     ```

4. **Networking Configuration**:
   - Ensure the VM is using a Bridged Adapter for networking.
   - Verify connectivity with other VMs in the homelab using `ping`.

5. **Setting Up Kubernetes**:
   - Initialize the Kubernetes cluster:
     ```bash
     sudo kubeadm init --pod-network-cidr=192.168.0.0/16
     ```
   - Set up kubeconfig for the non-root user:
     ```bash
     mkdir -p $HOME/.kube
     sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
     sudo chown $(id -u):$(id -g) $HOME/.kube/config
     ```

6. **Deploy a Pod Network**:
   - Deploy a pod network add-on (e.g., Calico):
     ```bash
     kubectl apply -f https://docs.projectcalico.org/v3.14/manifests/calico.yaml
     ```

## Usage
- Manage Kubernetes clusters and deploy containerized applications.

## Troubleshooting
- Check Kubernetes logs and Docker status if issues arise.

## Future Enhancements
- Scale the Kubernetes cluster with additional nodes.

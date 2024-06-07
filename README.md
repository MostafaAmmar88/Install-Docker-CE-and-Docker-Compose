# Docker CE and Docker Compose Installation Guide for CentOS 8

This guide provides step-by-step instructions to install Docker CE (Community Edition) and Docker Compose on a CentOS 8-based system, initiate the Docker service, and troubleshoot common issues.

## Prerequisites

- CentOS 8-based system
- User with sudo privileges

## Steps to Install Docker CE and Docker Compose

### 1. Set Up the Docker Repository

First, update the package index and install required packages:

```bash
sudo dnf -y install yum-utils

Next, add the Docker CE repository using the yum-config-manager tool:

Bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

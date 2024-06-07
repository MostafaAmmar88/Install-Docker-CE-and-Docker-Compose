# Docker CE and Docker Compose Installation Guide for CentOS 8

This guide provides step-by-step instructions to install Docker CE (Community Edition) and Docker Compose on a CentOS 8-based system. It also covers initiating the Docker service and troubleshooting common issues.

## Table of Contents

* [Installation](#installation)
* [Troubleshooting](#troubleshooting)

## Installation

1. **Set Up the Docker Repository**

   * Update the package list and install required tools:

     ```bash
     sudo dnf -y update dnf install yum-utils
     ```

   * Add the official Docker repository:

     ```bash
     sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
     ```

2. **Install Docker CE and Docker Compose**

   * Install Docker CE and containerd (container runtime):

     ```bash
     sudo dnf -y install docker-ce docker-ce-cli containerd.io
     ```

     **Note:** This installs the latest stable version. Refer to Docker documentation for specifics: [https://docs.docker.com/engine/install/centos/](https://docs.docker.com/engine/install/centos/)

   * Install Docker Compose:

     ```bash
     sudo dnf -y install curl
     sudo curl -L "https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
     sudo chmod +x /usr/local/bin/docker-compose
     ```

     This downloads the latest version (v2.3.3 in this example) from GitHub and places it in `/usr/local/bin`.

   * Verify Docker Compose installation:

     ```bash
     docker-compose --version
     ```

3. **Start and Enable Docker Service**

   * Start the Docker service:

     ```bash
     sudo systemctl start docker
     ```

   * Enable Docker to start on boot:

     ```bash
     sudo systemctl enable docker
     ```

   * Verify that Docker is running:

     ```bash
     sudo systemctl status docker
     ```

## Troubleshooting

While setting up Docker CE on a CentOS 8 system, you might encounter issues related to repository metadata errors. Errors such as:

To troubleshoot such issues:

* Clean Repository Cache:

  ```bash
  sudo dnf clean all


* Disable Problematic Repositories:

  ```bash
  sudo yum-config-manager --disable appstream base extras

* Add a Working Mirror:
* Comment MirrorList and uncomment baseurl:

* Modify the repository configuration file to use a working mirror:

  ```bash
  sudo vi /etc/yum.repos.d/CentOS-Stream-AppStream.repo
  sudo vi /etc/yum.repos.d/CentOS-Stream-BaseOS.repo
  sudo vi /etc/yum.repos.d/CentOS-Stream-Extras.repo
  sudo vi /etc/yum.repos.d/CentOS-Stream-Extras-common.repo

* Replace the 'baseurl' line with:

  ```ini
  baseurl=http://vault.centos.org/8-stream/AppStream/x86_64/os/

* Update the repository metadata:

  ```bash
  sudo dnf update

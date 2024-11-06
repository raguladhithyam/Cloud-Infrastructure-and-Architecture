# Exercise 1: Configure NOVA Compute Node

## Aim
To configure the NOVA Compute Node using OpenStack.

## Procedure

### Minimum Requirements
- A fresh Ubuntu 22.04 installation
- User with sudo privileges
- 4 GB RAM, 2 vCPUs, 10 GB Hard disk
- Internet connection

### Steps

1. **Update and Upgrade the System**
   - First, log into your Ubuntu 22.04 system using SSH protocol.
   - Update and upgrade the system repositories by executing:
     ```bash
     sudo apt update -y && sudo apt upgrade -y
     ```
   - Reboot the system with:
     ```bash
     sudo reboot
     ```

2. **Create a 'stack' User and Assign Sudo Privilege**
   - Create a new user named “stack” with sudo privileges for running DevStack.
   - Execute the following commands:
     ```bash
     sudo adduser -s /bin/bash -d /opt/stack -m stack
     sudo chmod +x /opt/stack
     echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
     ```

3. **Install Git and Download DevStack**
   - Switch to the "stack" user:
     ```bash
     su - stack
     ```
   - Install Git if it is not already installed:
     ```bash
     sudo apt install git -y
     ```
   - Clone DevStack’s Git repository:
     ```bash
     git clone https://git.openstack.org/openstack-dev/devstack
     ```

4. **Create DevStack Configuration File**
   - Navigate to the `devstack` directory and create a configuration file:
     ```bash
     cd devstack
     vim local.conf
     ```
   - Add the following configuration:
     ```
     [[local|localrc]]
     ADMIN_PASSWORD=StrongAdminSecret
     DATABASE_PASSWORD=$ADMIN_PASSWORD
     RABBIT_PASSWORD=$ADMIN_PASSWORD
     SERVICE_PASSWORD=$ADMIN_PASSWORD
     HOST_IP=10.208.0.10
     ```

5. **Install OpenStack with DevStack**
   - Run the installation script:
     ```bash
     ./stack.sh
     ```

6. **Access OpenStack on a Web Browser**
   - Use your Ubuntu’s IP address:
     ```
     https://server-ip/dashboard
     ```
   - Log in with the default username “admin” and the ADMIN_PASSWORD.

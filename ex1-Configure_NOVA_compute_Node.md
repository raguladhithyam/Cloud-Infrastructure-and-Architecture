
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

1. **Update and Upgrade System**
    ```bash
    apt update -y && apt upgrade -y
    sudo reboot
    ```

2. **Create Stack User and Assign Sudo Privilege**
    ```bash
    sudo adduser -s /bin/bash -d /opt/stack -m stack
    sudo chmod +x /opt/stack
    echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
    ```

3. **Install Git and Download DevStack**
    ```bash
    sudo apt install git -y
    git clone https://git.openstack.org/openstack-dev/devstack
    ```

4. **Create DevStack Configuration File**
    ```bash
    cd devstack
    vim local.conf
    ```

5. **Install OpenStack with DevStack**
    ```bash
    ./stack.sh
    ```

6. **Accessing OpenStack on a Web Browser**
    - Use: https://server-ip/dashboard
    

# Exercise 4: Build a Horizon Node

## Aim
To build a Horizon monitor node.

## Procedure

1. **Install OpenStack Dashboard**
    ```bash
    apt install openstack-dashboard
    ```

2. **Configure the Dashboard** by editing `/etc/openstack-dashboard/local_settings.py`.
3. **Reload Web Server** to finalize the installation.
    ```bash
    systemctl reload apache2.service
    ```
    
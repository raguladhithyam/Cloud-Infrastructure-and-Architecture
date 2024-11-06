# Ex.No: 03 - Construct a Cinder Block Node

## Aim
To install and configure the Block Storage service, code-named Cinder, on the controller node. This service requires at least one additional storage node that provides volumes to instances.

---

## Prerequisites
Before installing and configuring the Block Storage service, you must set up a database, service credentials, and API endpoints.

---

### 1. Create the Database

1. Connect to the database server as the root user:
    ```bash
    mysql
    ```

2. Create the cinder database:
    ```sql
    CREATE DATABASE cinder;
    ```

3. Grant access to the cinder database:
    ```sql
    GRANT ALL PRIVILEGES ON cinder.* TO 'cinder'@'localhost' IDENTIFIED BY 'CINDER_DBPASS';
    GRANT ALL PRIVILEGES ON cinder.* TO 'cinder'@'%' IDENTIFIED BY 'CINDER_DBPASS';
    ```
    Replace `CINDER_DBPASS` with a secure password.

4. Exit the database access client.

---

### 2. Set up Service Credentials

1. Source the admin credentials:
    ```bash
    . admin-openrc
    ```

2. Create a cinder user:
    ```bash
    openstack user create --domain default --password-prompt cinder
    ```

3. Add the admin role to the cinder user:
    ```bash
    openstack role add --project service --user cinder admin
    ```

4. Create the cinderv3 service entity:
    ```bash
    openstack service create --name cinderv3 --description "OpenStack Block Storage" volumev3
    ```

---

### 3. Create Block Storage Service API Endpoints

1. Create public endpoint:
    ```bash
    openstack endpoint create --region RegionOne volumev3 public http://controller:8776/v3/%\(project_id\)s
    ```

2. Create internal endpoint:
    ```bash
    openstack endpoint create --region RegionOne volumev3 internal http://controller:8776/v3/%\(project_id\)s
    ```

3. Create admin endpoint:
    ```bash
    openstack endpoint create --region RegionOne volumev3 admin http://controller:8776/v3/%\(project_id\)s
    ```

---

## Install and Configure Components

1. Install required packages:
    ```bash
    apt install cinder-api cinder-scheduler
    ```

2. Edit the `/etc/cinder/cinder.conf` file:

    - Configure database access in `[database]` section:
      ```ini
      [database]
      connection = mysql+pymysql://cinder:CINDER_DBPASS@controller/cinder
      ```
      Replace `CINDER_DBPASS` with the chosen password.

    - Configure RabbitMQ message queue in `[DEFAULT]` section:
      ```ini
      [DEFAULT]
      transport_url = rabbit://openstack:RABBIT_PASS@controller
      ```
      Replace `RABBIT_PASS` with the RabbitMQ password.

    - Configure Identity service access in `[DEFAULT]` and `[keystone_authtoken]` sections:
      ```ini
      [DEFAULT]
      auth_strategy = keystone

      [keystone_authtoken]
      www_authenticate_uri = http://controller:5000
      auth_url = http://controller:5000
      memcached_servers = controller:11211
      auth_type = password
      project_domain_name = default
      user_domain_name = default
      project_name = service
      username = cinder
      password = CINDER_PASS
      ```
      Replace `CINDER_PASS` with the cinder user's password.

    - Configure the management IP address in `[DEFAULT]` section:
      ```ini
      [DEFAULT]
      my_ip = 10.0.0.11
      ```

    - Configure lock path in `[oslo_concurrency]` section:
      ```ini
      [oslo_concurrency]
      lock_path = /var/lib/cinder/tmp
      ```

3. Populate the Block Storage database:
    ```bash
    su -s /bin/sh -c "cinder-manage db sync" cinder
    ```

---

## Configure Compute to Use Block Storage

1. Edit the `/etc/nova/nova.conf` file and add the following:
    ```ini
    [cinder]
    os_region_name = RegionOne
    ```

---

## Finalize Installation

1. Restart the Compute API service:
    ```bash
    service nova-api restart
    ```

2. Restart Block Storage services:
    ```bash
    service cinder-scheduler restart
    service apache2 restart
    ```

---

**Note**: Replace placeholder passwords and IP addresses with your specific environment values.

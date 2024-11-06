# Exercise 3: Construct a Cinder Block Node

## Aim
To install and configure the Block Storage service, also known as "Cinder," on the controller node.

## Procedure

### Steps

1. **Create the Cinder Database**
   - Log into the database server as the root user:
     ```bash
     mysql -u root -p
     ```
   - Create the Cinder database and grant privileges:
     ```sql
     CREATE DATABASE cinder;
     GRANT ALL PRIVILEGES ON cinder.* TO 'cinder'@'localhost' IDENTIFIED BY 'CINDER_DBPASS';
     GRANT ALL PRIVILEGES ON cinder.* TO 'cinder'@'%' IDENTIFIED BY 'CINDER_DBPASS';
     ```
   - Replace `CINDER_DBPASS` with a suitable password.

2. **Create the Service User and API Endpoints**
   - Create a user with OpenStack CLI:
     ```bash
     openstack user create --domain default --password-prompt cinder
     ```
   - Set up the Block Storage service API endpoints for `volumev3`.

3. **Install and Configure Components**
   - Install Cinder packages:
     ```bash
     sudo apt install cinder-api cinder-scheduler
     ```
   - Configure `/etc/cinder/cinder.conf` with database, RabbitMQ, and Identity service settings.

4. **Restart Services**
   - After configuration, restart Cinder and Nova services:
     ```bash
     service nova-api restart
     service cinder-scheduler restart
     service apache2 restart
     ```

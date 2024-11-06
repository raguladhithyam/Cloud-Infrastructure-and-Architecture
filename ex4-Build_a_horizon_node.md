
# Exercise 4: Build a Horizon Node

Overview

This guide describes how to install and configure the OpenStack Horizon dashboard on the controller node.

Prerequisites

- Proper installation, configuration, and operation of the Identity service using Apache HTTP server and Memcached service.

Installation Steps

Install Packages


bash
sudo apt install openstack-dashboard


Configure Dashboard

/etc/openstack-dashboard/local_settings.py


# Configure dashboard to use OpenStack services on controller node
OPENSTACK_HOST = "controller"

# Allow hosts to access Dashboard
ALLOWED_HOSTS = ['(link unavailable)', '(link unavailable)']

# Configure memcached session storage service
SESSION_ENGINE = 'django.contrib.sessions.backends.cache'
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.memcached.MemcachedCache',
        'LOCATION': 'controller:11211',
    }
}

# Enable Identity API version 3
OPENSTACK_KEYSTONE_URL = "http://%s/identity/v3" % OPENSTACK_HOST

# Enable support for domains
OPENSTACK_KEYSTONE_MULTIDOMAIN_SUPPORT = True

# Configure API versions
OPENSTACK_API_VERSIONS = {
    "identity": 3,
    "image": 2,
    "volume": 3,
}

# Configure default domain and role
OPENSTACK_KEYSTONE_DEFAULT_DOMAIN = "Default"
OPENSTACK_KEYSTONE_DEFAULT_ROLE = "user"

# Disable layer-3 networking services (if networking option 1)
OPENSTACK_NEUTRON_NETWORK = {
    ... 
    'enable_router': False,
    'enable_quotas': False,
    'enable_ipv6': False,
    'enable_distributed_router': False,
    'enable_ha_router': False,
    'enable_fip_topology_check': False,
}

# Optionally, configure time zone
TIME_ZONE = "TIME_ZONE"  # Replace with appropriate time zone identifier


/etc/apache2/conf-available/openstack-dashboard.conf


bash
WSGIApplicationGroup %{GLOBAL}


Finalize Installation


bash
sudo systemctl reload apache2.service

Role Name
=========

Some Linux Hardening for raspberry pi running Raspian.

Role Variables
--------------

* **pi_user** variable is a map with **username** and **shell** keys. This is the user that will be replacing pi user.  
  * **username** defaults to _raspiuser_  
  * **shell** defaults to _/bin/bash_  

* **ssh_port** replaces the default 22 ssh port, defaults to _3102_.

* **service_packages** is a list holding any packages that need to be installed and start as a service at boot. Defaults to _fail2ban_ and _ufw_

Example Playbook
----------------

To use the role, define it in your playbook:

    - hosts: pis
      roles:
         - { role: rmiguelac.raspberry-hardening }

License
-------

Apache License 2.0

Author Information
------------------

Created by Rui Miguel Andrade Constâncio.

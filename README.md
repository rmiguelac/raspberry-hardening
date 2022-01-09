rpihardening
=========

Some Linux Hardening for raspberry pi running Raspian.

**Role Variables**
--------------

* **pi_user** variable is a map with **username**, **password** and **shell** keys. This is the user that will be replacing pi user.  
  * **username** defaults to _raspiuser_  
  * **shell** defaults to _/bin/bash_  
  * **password** defautls to '', yet **_SHOULD ALWAYS_** be overwritten, otherwise access to root account will be lost.

* **ssh_port** replaces the default 22 ssh port, defaults to _3102_.

* **service_packages** is a list holding any packages that need to be installed and start as a service at boot. Defaults to _fail2ban_ and _ufw_

**Example Playbook**
----------------

To use the role, define it in your playbook:

_hardening.yaml_

```
---
- hosts: pis
  roles:
  - role: rmiguelac.rpi-hardening
    vars:
      pi_user:
        username: mypiuser
        shell: /bin/bash
        password: 'oHhmy4pass!nDGIT'
```

**Testing**
-------

First we run [yamllint](https://yamllint.readthedocs.io/en/stable/) with:

```bash
yamllint .
```

Then we perform the syntax check with:

```bash
ansible-playbook hardening.yaml --syntax-check
```

Also, for good measure we run ansible-lint:

```
ansible-lint .
```

Lastly, [Molecule](https://molecule.readthedocs.io/en/latest/)

**License**
-------

Apache License 2.0

**Author Information**
------------------

Created by Rui Miguel Andrade Constâncio in 2022.

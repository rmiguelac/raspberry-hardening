rpihardening
=========

Some Linux Hardening for raspberry pi running Raspian.

**Role Variables**
--------------

| variable                 | context                                                                     | default                                                         |
| ------------------------ | --------------------------------------------------------------------------- | --------------------------------------------------------------- |
| **pi_user**.**username** | This is the user that will be replacing pi user.                            | defaults to _raspiuser_                                         |
| **pi_user**.**shell**    | New user shell                                                              | defaults to _/bin/bash_                                         |
| **pi_user**.**password** | New user password                                                           | defautls to _'myeasyP@ss123'_                                   |
| **ssh_port**             | Replaces the default 22 ssh port                                            | defaults to _3102_.                                             |
| **services**             | List of packages that will be installed and should start at boot (services) | Defaults to _fail2ban_ and _ufw_                                |
| **packages**             | List of packages that will be installed                                     | Defaults to _unattended-upgrades, apt-listchanges and apticron_ |

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

For molecule to use vagrant, we must install molecule-vagrant, like:

```
pip3 install molecule-vagrant
```

**License**
-------

Apache License 2.0

**Author Information**
------------------

Created by Rui Miguel Andrade Constâncio in 2022.

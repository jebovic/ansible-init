Init
====

[![Build Status](https://travis-ci.org/jebovic/ansible-init.svg?branch=master)](https://travis-ci.org/jebovic/ansible-init) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.init-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/init)

Default init role for needed stuff on all servers

This role is a part of my [OPS project](https://github.com/jebovic/ops), follow this link to see it in action. OPS provides a lot of stuff, like a vagrant file for development VMs, playbooks for roles orchestration, inventory files, examples for roles configuration, ansible configuration file, and many more.

Role Variables
--------------

```yaml
# timezone configuration
update_timezone: yes
timezone_name: Europe/Paris

# Default apt packages to install
init_apt_packages:
  - vim
  - curl
  - wget
  - htop
  - ntp
  - logrotate
  - unzip
  - sendmail-bin
  - sendmail

# /etc/hosts configuration
update_host_file: yes
custom_hosts: []

# Pip configuration
pip_enabled: yes
pip_download_url: https://bootstrap.pypa.io/get-pip.py
pip_download_dest: /tmp
pip_version: latest
python: python
pip: pip

# Default pip packages to install
init_pip_packages:
  - httpie

# ntp basic configuration
ntp_enabled: yes
ntp_servers:
  - 0.fr.pool.ntp.org
  - 1.fr.pool.ntp.org
  - 2.fr.pool.ntp.org
  - 3.fr.pool.ntp.org
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - { role: jebovic.init }
```

Tags
----

* timezone_config : only update server timezone
* etc_hosts_config : only update /et/hosts file
* ntp : configure and restart ntp
* ntp_config : only update config and restart service
* pip : install pip

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic

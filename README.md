Role Name
=========

Wordpress installer

Requirements
------------

No special requirements; note that this role requires root access, so either run it in a playbook with a global become: yes, or invoke the role in your playbook like:

- hosts: wp
  roles:
    - certificate #installs selfsigned cert
    - geerlingguy.nginx 
    - geerlingguy.php
    - geerlingguy.mysql
    - wordpress
      become: yes


Role Variables
--------------

Variables sets in vars/wordpress

Dependencies
------------

The role uses the following roles:

https://galaxy.ansible.com/geerlingguy/nginx

https://galaxy.ansible.com/geerlingguy/php

https://galaxy.ansible.com/geerlingguy/mysql

Install them before using

ansible-galaxy install geerlingguy.nginx geerlingguy.mysql geerlingguy.php

Example Playbook
----------------

---
- hosts: wp

  vars_files:
    - vars/wordpress.yml 
  roles:
    - certificate #installs selfsigned cert if needed
    - geerlingguy.nginx 
    - geerlingguy.php
    - geerlingguy.mysql
    - wordpress


License
-------

MIT

Author Information
------------------

https://github.com/Vladarbinyan/

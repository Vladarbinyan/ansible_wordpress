Role Name
=========

A brief description of the role goes here.

Requirements
------------



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
- hosts: all

  vars_files:
    - vars/wordpress.yml 
  roles:
    - certificate #installs selfsigned cert
    - geerlingguy.nginx 
    - geerlingguy.php
    - geerlingguy.mysql
    - wordpress


License
-------

MIT

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

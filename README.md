Role Name
=========

Wordpress installer

Requirements
------------

For test with local SSL cert you can add to playbook next sentences

  vars_files:
    - ~/ansible/roles/wordpress/vars/wordpress.yml 
    - ~/ansible/roles/wordpress/vars/vault.yml
  tasks:
  - name: Install self signed SSL cert
    tags: [certificate]
    import_tasks: ~/ansible/roles/wordpress/tasks/self_signed_ssl.yml
    when: generate_local_cert
  roles:
    - { role: geerlingguy.nginx, tags: [nginx] } 
    - { role: geerlingguy.php, tags: [php] }
    - { role: geerlingguy.mysql, tags: [mysql] } 
    - { role: wordpress, tags: [mysql] }




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

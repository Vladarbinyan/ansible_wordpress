Role Name
=========

Wordpress installer

Requirements
------------

For test with local SSL cert you can add to playbook next sentences

---
- name: Generate pk
  openssl_privatekey:
    path: '{{ ssl_cert_path }}/private/{{ server_name }}.pem'
    size: 2048 

- name: Generate an OpenSSL Certificate Signing Request
  openssl_csr:
    path: '{{ ssl_cert_path }}/csr/{{ server_name }}.csr'
    privatekey_path: '{{ ssl_cert_path }}/private/{{ server_name }}.pem'
    common_name: '{{ server_name }}'

- name: Generate a Self Signed OpenSSL certificate
  openssl_certificate:
    path: '{{ ssl_cert_path }}/crt/{{ server_name }}.crt'
    privatekey_path: '{{ ssl_cert_path }}/private/{{ server_name }}.pem'
    csr_path: '{{ ssl_cert_path }}/csr/{{ server_name }}.csr'
    provider: selfsigned




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

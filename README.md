[![Build Status](https://travis-ci.com/1mr/ansible-role-zabbix-host.svg?branch=master)](https://travis-ci.com/1mr/ansible-role-zabbix-host)

Zabbix-host
===========

This role helps to create, modify and delete zabbix host entries and associated group and template data.  

Requirements
------------

This role requires ansible 2.5 or higher.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows:

Server:

    zabbix_server: http://zabbix.lcl
    zabbix_server_user: zabbix
    zabbix_server_password: zabbix

Host:

    zabbix:
      hostname: www.example.com
      ip: 10.10.10.10
      port: 10050
      groups:
        - linux
        - web
      templates:
        - linux
        - nginx
      proxy: proxy
      status: enabled
      state: present
      macros:
        name:
          - MYSQL_HOST
        value:
          - db.example.com

Default values for optional variables:

    hostname: {{ inventory_hostname }}
    ip: {{ ansible_ssh_host }}
    port: 10050

Dependencies
------------

Packages (pip):

- zabbix-api

Example Playbook
----------------

    - hosts: servers
      roles:
        - { role: 1mr.zabbix-host, tags: zabbix-host, become: no }

License
-------

MIT

Author Information
------------------

This role was created by Stas Stavnichuk.

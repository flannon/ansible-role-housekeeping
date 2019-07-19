Housekeeping Role
=========

Installs base packages and configuration for NYU DLTS servers.

Requirements
------------

Tested on Centos 7

Role Variables
--------------

List of standard packages to install. Full list can be found in defaults/main.yml

    housekeeping_standard_packages:
      - git

List of TCP ports to allow through firewalld

    housekeeping_firewall_allowed_ports:
      - 22

Server environment. Affects how automatic updates are applied. 

    housekeeping_server_env: dev

Level of automatic updates to apply using yum-cron. 

    housekeeping_yum_cron_update_cmd: security

Whether yum-cron should send update messages.

    housekeeping_yum_cron_update_messages: "{{ 'yes' if housekeeping_server_env=='dev' else 'no' }}"

Whether yum-cron should automatically download available updates.

    housekeeping_yum_cron_download_updates: "{{ 'yes' if housekeeping_server_env=='dev' else 'no' }}"

Whether yum-cron should automatically apply downloaded updates.

    housekeeping_yum_cron_apply_updates: "{{ 'yes' if housekeeping_server_env=='dev' else 'no' }}"

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - ansible-role-housekeeping

License
-------

BSD

Author Information
------------------

Created by NYU DLTS

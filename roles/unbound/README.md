Unbound Role
=========

Use this role to install unbound plus ad blocking black list on a home lab bastion server.

Requirements
------------

This play uses a minimal install if RHEL8 or Fedora.

Role Variables
--------------

Three variables are used.  net_mask in the defaults section for the jinja template so the access-control can be set to allow local subnets. domain_name in the play_vars.yml global variable plus services and packages in the vars folder.

Dependencies
------------

python3-netaddr

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

---
- name: Bastion Setup
  hosts: bastion
  vars_files:
    - play_vars.yml
  roles:
    - unbound

License
-------

GPL

Author Information
------------------

https://ericlajoie.com

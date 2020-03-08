haproxy
=========

Install haproxy on the bastion and set selinux rules to allow port binding

Requirements
------------

the ansible controller needs to have rhel-system-roles or linux-system-roles

Role Variables
--------------

Services and Ports are for the firewall.
Packages are for the tools needed to look at SELinux settings and HAProxy itself.
The other vars are all related to the rhel-system-role.selinux role.

Dependencies
------------

haproxy


License
-------

GPL

Author Information
------------------

https://ericlajoie.com

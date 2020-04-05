# Ansible-Lab
Ansible based install and setup of OCP and other tools for the bastion nodes.

1. create a .gitignore file with the follwoing
- .gitignore
- inventory
- vault

1.1. install packages needed
- rhel-system-roles
- python3-netaddr

2. create your inventory file
- add both bastiomn and kvm nodes

3. create vault file with your vault_rhn_password variable

4. Install rhel-system-roles

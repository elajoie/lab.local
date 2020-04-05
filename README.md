# Ansible-Lab to learn Ansible while installing OCP via UPI
This document is intended for SAs and SSAs who are moving from OpenStack experience towards a focus on OKE/OCP. All tasks are done in Ansible from a laptop.

![Lab Diagram](Demo%20Basics.jpg)

Playbooks can be found here:
https://github.com/elajoie/lab.local

Most of the Ansible is basic and fits well with someone who has just finished the EX294 exam.

# Setup Bation (Manual)
In this section you will set up the bastion which is used to stage many network services including PXE booting of KVM nodes. Grab the latest version of RHEL8 (8.2 Beta for this version) and put it on a USB to boot your bastion HW off of. All the HW in my topology is set up on VLAN1 and VLAN2 with the 192.168.1.0/24 network on VLAN1.

1. Install minimal server version and register with RH
1. get the latest RHEL8 boot iso and put it in the files folder in the pxe role
1. update the variables in the defaults folder for this role to match the iso
1. create a .gitignore file with the following
   1. .gitignore
   1. inventory
   1. vault
1. install packages needed on your laptop running the playbooks
   1. rhel-system-roles
   1. python3-netaddr
1. create vault file with these variable:
   1. vault_rhn_username: RHNusername
   1. vault_rhn_password: neverEndingShadow
   1. vault_orgid: sevenDigitOrgID
   1. vault_actkey: keyNameYouCreate
   1. vault_rootpasswd: changeme
   1. vault_kvm02_user: redfish (optional)
   1. vault_kvm02_pass: changeme (optional)
   1. vault_token_long: "long secret"
   1. vault_sshkey: "ssh-rsa AAAA"

1. Run 01bastion.yml to setup all the services
1. Once this play is done you should be able to PXE boot your KVM nodes
1. You also have an optional role called redfish if you have redfish support in your KVM nodes to automate the reboot and boot mode setting to PXE via APIs

1. Run 02kvm.yml roles when all the kvm nodes have done rebooting
1. For now just manually start the VMs once they are all off and the OCP install should finish on its own
1. Shut down the bootstrap node
#On bastion: 
1. export KUBECONFIG=/opt/registry/www/html/ignition/auth/kubeconfig
1. oc get nodes
1. oc patch configs.imageregistry.operator.openshift.io cluster --type merge --patch '{"spec":{"storage":{"emptyDir":{}}}}'
1. oc get clusterversion; echo; oc get clusteroperators 

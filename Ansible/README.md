# OS: 
Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-52-generic x86_64)

# Ansible & Infoblox Integration - Deployment Guide
https://www.infoblox.com/wp-content/uploads/infoblox-deployment-guide-infoblox-and-ansible-integration.pdf

# Before using Ansible nios modules with Infoblox, you must install the "infoblox-client" on your Ansible control node:
pip3 install infoblox-client
Follow & install "requirements.txt".

# During "infoblox-client" installation, *might* have to uninstall old packages of following...
pyinotify
netaddr
PyYAML

# Uninstall them with older PIP version, then upgrade the PIP to newest version.
pip install pip==8.1.1
pip uninstall pyinotify pyinotify netaddr PyYAML
pip install --upgrade pip


# To use Infoblox nios modules in playbooks, you need to configure the credentials to access your Infoblox system. The examples in this guide use credentials stored in <playbookdir>/group_vars/nios.yml. Replace these values with your Infoblox credentials:
---
provider:
  host: <infoblox/grid_IP> # string, without brackets
  username: <username> # string, without brackets
  password: <password> # string, without brackets

NOTE: Might have to update ansible-controller hosts file with NIOS IP Address based on the inventory file config.

# You must run the NIOS lookup plugins locally by specifying 
connection: local

# install Infoblox nios_module from Ansible Galaxy.
ansible-galaxy collection install community.general
The collection folder would be installed at ~/.ansible/collections/ansible_collections/infoblox/nios_modules

# Ansible-Galaxy Collection Modules
https://docs.ansible.com/ansible/latest/collections/community/general/
search for nios_xxx_modules >> 'xxx' is DNS record type, eg: CNAME, AAAA, A, TXT, etc
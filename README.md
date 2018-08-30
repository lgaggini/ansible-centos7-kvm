# ansible-centos7-kvm

ansible-centos7-kvm is an Ansible playbook to bootstrap a centos 7 server to be used as kvm hypervisor. It performs some basic configuration
and basic hardening (first n minutes on an new server like) on the server and it installs and configure a basic kvm hypervisor.
It has a very limted scope, it's modeled on an Hetzner dedicated server and it has a quite strict configuration for kvm storage
pools and networks (more in the configuration part of this readme)

It configures by distinct roles:

* basic users
* ssh
* basic packages
* motd
* fail2ban
* firewall
* mail for notifications
* unattended updates by yum-cron
* libvirt and kvm

## Install
### Clone
```bash
git clone https://github.com/lgaggini/ansible-centos7-kvm.git
```
## Configuration

The configuration is done by the group_vars/all file. User password can be set by use Ansible Vault.
Options are self-explanatory (maybe).

## Usage

ansible-playbook -i hosts playbook.yml --tags {{ tag }}

Available tags are:

* user
* ssh
* packages
* motd
* fail2ban
* firewall
* mail
* yum-cron
* libvirt-kvm

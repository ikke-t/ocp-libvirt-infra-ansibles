# ocp-libvirt-infra-ansibles

This is ansible automation for creating RHEL virtual machines on libvirt host.

Personally I use this to setup demoes for OpenShift. I use this ansible to create OpenShift cluster virtual machines on top of generic libvirt host (RHEL7/CentOS7).

# Usage

1. Do git clone this repo.
2. Download RHEL KVM image and save it to: ```playbooks/roles/virt-host/files/rhel-7-kvm.qcow2```. You get it here for free: https://access.redhat.com/downloads/content/69/ver=/rhel---7/latest/x86_64/product-software
3. Create a settings file into: `playbooks/vars/main.yml`. There is example file available: `playbooks/vars/example-main.yml`
4. you can add and remove hosts by adding entries into virtual_machines table in the above settings file
5. run ansible to setup the host: `ansible-playbook -i hosts do-host.yml`
6. run ansible to setup the guests: `ansible-playbook -i hosts do-guests.yml`
7. you can cleanup all guest stuff: `ansible-playbook -i hosts nuke-guests.yml`

There is a dirty trick done to get networking right, I'll try to make it nicer. Please PR if you know how to get cloud-init to set static addresses so that routes and name resolution work too.

BR,
ikke

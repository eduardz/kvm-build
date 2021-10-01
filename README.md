Deploy new VMs with virt-builder.

Set the kvm server in inventory file

#####
Setup VM (name, ram, cpu, storage, OS flavor in vms.yml

vms.yml example


get template names with virt-builder --list

example:
os_template: fedora-34
os_template: centos-8.2
os_template: centos-7.8

###
guests:
  kube_master:
    mem: 1024
    cpus: 1
    os_template: centos-8.2
    os_type: linux
    file_type: qcow2
    disk_size: 8G
  kube_slave01:
    mem: 1024
    cpus: 1
    os_template: centos-7.8
    os_type: linux
    file_type: qcow2
    disk_size: 12G
###

# deply VMs with password
ansible-playbook -i inventory kvm.yml -K 


# deply VMs with public key
ansible-playbook -i inventory kvm.yml 



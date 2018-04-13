# kubernetes-kvm-poc

A Kubernetes cluster PoC running on KVM.

## Prerequisites
- Install libvirt
- Uncomment "host_key_checking = false" in /etc/anisble/ansible.cfg

## Install VMs
You need to have the libvirt default network virbr0 192.168.122.0/24 active to be able to run the install-vms.yml playbook

```
$ ansible-playbook install-vms.yml -K
```
During the installation the user "ubuntu" is created with the password "ubuntu"

When installation is done the VMs will be shutdown and you can then re-run the command above to boot the guests.

## Install Kubernetes and create an active cluster running Weave Cloud

```
$ ansible-playbook setup-kubernetes.yml -i inventory -k -K
```

You should now have a working Kubernetes cluster.
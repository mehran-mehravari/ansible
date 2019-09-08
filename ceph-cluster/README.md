## Purpose

Setup a Ceph cluster (Mimic version)for the orchestration of the storage layer

## Prerequisites

1. Get Ansible from [http://docs.ansible.com/ansible/latest/intro_installation.html](http://docs.ansible.com/ansible/latest/intro_installation.html)

2. Setup the infrastructure

In this first version, I've only tested with Centos-7 x86-64
* one manager used to deploy a Ceph cluster
* three nodes participating to the Ceph cluster
* copy ansible machine public ssh key to all nodes
* Attach an empty disk to each compute nodes in order to create OSD block

## Test machines

Make sure the machine can be accessed

```
$ ansible -i inventory.ini -u root -m ping all

ceph-controller | SUCCESS => {
    "changed": false,
    "failed": false,
    "ping": "pong"
}
ceph-monitor | SUCCESS => {
    "changed": false,
    "failed": false,
    "ping": "pong"
}
ceph-compute01 | SUCCESS => {
    "changed": false,
    "failed": false,
    "ping": "pong"
}
ceph-compute02 | SUCCESS => {
    "changed": false,
    "failed": false,
    "ping": "pong"
}
```

## Deploy

The cluster can be deployed with the following command

```
$ ansible-playbook -i inventory.ini -u root playbook.yml

## Results

3 nodes provides Ceph cluster

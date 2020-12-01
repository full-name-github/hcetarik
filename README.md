# hcetarik

**This is just a draft.**

## Setup

*Vagrantfile*, when executed with *vagrant*, starts 3 vms:

- *vm0* is the vm running *ansible* (i.e. running the file *playbook.yml* with *ansible-playbook*)
- *vm1* and *vm2* are the actual "docker nodes", in particular
    - *vm1* is a "docker worker"
    - *vm2* is a "docker manager"

The docker swarm is created by the ansible role *atosatto.docker-swarm*.

## Instructions

1. `vagrant plugin install vagrant-disksize` (to install the *vagrant-disksize* plugin)
2. `vagrant up` (to start Vagrant)
3. `vagrant ssh vmN` (to ssh into the vms; `N` is `1`, `2` or `3`; useful when `N` is `1`, since *vm1* is a "docker manager")

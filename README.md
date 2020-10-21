# Ansible Collection - ekultails.lab_openstack

This projects provides a collection of Ansible content for helping to set up an OpenStack cloud using RDO packages. For more roles specific to TripleO, consider using the official [tripleo-operator-ansible collection](https://opendev.org/openstack/tripleo-operator-ansible).


## Install

Latest development:

```sh
$ git clone https://github.com/ekultails/ansible_collection_lab_openstack.git
$ cd ansible_collection_lab_openstack
$ ansible-galaxy collection build --force
$ ansible-galaxy collection install --force ekultails-lab_openstack-*.tar.gz
```

Stable release from Ansible Galaxy:

```sh
$ ansible-galaxy collection install ekultails.lab_openstack
```

Roles are available using the namespace `ekultails.lab_openstack.<ROLE_NAME>`.


## Supported Environments

* TripleO Queens, Rocky, Stein, Train, and Ussuri.
* RHOSP 13 and 16.


## Roles

* [rdo_packages](roles/rdo_packages/README.md) = Enable OpenStack repositories.
* [tripleo_heat_templates](roles/tripleo_heat_templates/README.md) = Render Heat templates with parameters for a basic deployment.
* [undercloud](roles/undercloud/README.md) = Prep and install the Undercloud.

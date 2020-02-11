# Ansible Collection - ekultails.ansible_collection_lab_openstack

This projects provides a collection of Ansible content for helping to set up an OpenStack cloud using RDO packages. For more roles specific to TripleO, consider using the official [tripleo-operator-ansible collection](https://opendev.org/openstack/tripleo-operator-ansible).


## Install

```sh
ansible-galaxy collection build --force
ansible-galaxy collection install --force ekultails-ansible_collection_lab_openstack-*.tar.gz
```

Roles are available using the namespace `ekultails.ansible_collection_lab_openstack.<ROLE_NAME>`.


## Supported Environments

* TripleO Queens, Rocky, Stein, and Train
* RHOSP 13 and 14


## Roles

* [rdo_packages](roles/rdo_packages/README.md) = Enable OpenStack repositories.
* [tripleo_heat_templates](roles/tripleo_heat_templates/README.md) = Render Heat templates with parameters for a basic deployment.
* [undercloud](roles/undercloud/README.md) = Prep and install the Undercloud.

# ansible_role_rdo_packages

A role to configure and install RDO packages for OpenStack on Red Hat distributions.

## Requirements

* Ansible >= 2.9

## Dependencies

None.

## Role Variables

* rdo_packages_openstack_release (string) = The OpenStack release to setup on the Undercloud. For upstream packages, this should be the release name. For downstream packages, this should be the major RHOSP version.
    * Upstream (TripleO) = `queens`, `rocky`, `stein`, `train`, or `ussuri`.
    * Downstream (RHOSP) = `13` or `16`.
* rdo_packages_openstack_repo (string) = The OpenStack RPM repository to use: `centos`, `rdo`, or `rhosp`.
* rdo_packages_rdo_branch (string) = The RDO branch to use: `consistent`, `current`, `current-tripleo`, or `current-tripleo-rdo` (default).
* rdo_packages_centos_version (string) = For the `rdo` repo only. The major CentOS version to use.
    * < Train = Use `7`.
    * Train = Use `7` or `8` (recommended).
    * \> Train = Use `8`.
* rdo_packages_rh_user (string) = Username for Red Hat subscriptions.
* rdo_packages_rh_pass (string) = Password for Red Hat subscriptions.
* rh_user (string) = The Red Hat user for subscription-manager.
* rh_pass (string) = The Red Hat user's password for subscription-manager.

## Example Playbook

Upstream:

```
---
- hosts: undercloud
  roles:
    - name: rdo_packages
      vars:
        rdo_packages_openstack_release: master
        rdo_packages_rdo_branch: current
        rdo_packages_centos_version: 8
```

Downstream:

```
---
- hosts: undercloud,overcloud
  roles:
    - name: rdo_packages
      vars:
        rdo_packages_openstack_repo: rhosp
        rdo_packages_openstack_release: 13
        rdo_packages_rh_user: example
        # This password should be stored in a Vault encrypted file.
        rdo_packages_rh_pass: example123
```

## License

Apache v2.0

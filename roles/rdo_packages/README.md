# ansible_role_rdo_packages

A role to configure and install RDO packages for OpenStack on Red Hat distributions.

## Requirements

* Ansible >= 2.7

## Dependencies

None.

## Role Variables

* rdo_packages_openstack_release = The OpenStack release to setup on the Undercloud. For upstream packages, this should be the release name. For downstream packages, this should be the RHOSP version. Default: rocky.
* rdo_packages_openstack_repo = The OpenStack RPM repository to use: `centos`, `rdo`, or `rhosp`. Default: `rdo`.
* rdo_packages_rh_user = Username for Red Hat subscriptions.
* rdo_packages_rh_pass = Password for Red Hat subscriptions.

## Example Playbook

Upstream:

```
---
- hosts: undercloud
  roles:
    - rdo_packages
```

Downstream:

```
---
- hosts: undercloud,overcloud
  roles:
    - name: rdo_packages
      vars:
        rdo_packages_openstack_repo: rhosp
        rdo_packages_openstack_release: 14
        rdo_packages_rh_user: example
        # This password should be stored in a Vault encrypted file.
        rdo_packages_rh_pass: example123
```

## License

Apache v2.0

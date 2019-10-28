# ansible_role_undercloud

A role to configure and install the Undercloud as part of an OpenStack deployment using TripleO.

## Requirements

* Ansible >= 2.7

## Dependencies

None.

## Role Variables

* openstack_release = The OpenStack release to setup on the Undercloud. For upstream packages, this should be the release name. For downstream packages, this should be the RHOSP version. Default: rocky.
* openstack_repo = The OpenStack RPM repository to use: `centos`, `rdo`, or `rhosp`. Default: `rdo`.
* rh_user = Username for Red Hat subscriptions.
* rh_pass = Password for Red Hat subscriptions.
* tripleo_undercloud_install = If the "openstack undercloud install" command should be executed. Default: `false`.
* tripleo_undercloud_upload_images = If the Overcloud kernel, initramfs, and QCOW2 image should be automatically downloaded and uploaded to Glance. Default: `false`.
* tripleo_undercloud_config = Custom configurations for the Undercloud.

## Example Playbook

Upstream:

```
---
- hosts: undercloud
  roles:
    - ansible_role_tripleo_undercloud
```

Downstream:

```
---
- hosts: undercloud
  roles:
    - name: ansible_role_tripleo_undercloud
      vars:
        openstack_repo: rhosp
        openstack_release: 14
        rh_user: example
        # This password should be stored in a Vault encrypted file.
        rh_pass: example123
```

## License

Apache v2.0

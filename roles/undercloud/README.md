# ansible_role_undercloud

A role to configure and install the Undercloud as part of an OpenStack deployment using TripleO.

## Requirements

* Ansible >= 2.7

## Dependencies

None.

## Role Variables

* undercloud_install = If the "openstack undercloud install" command should be executed. Default: `false`.
* undercloud_upload_images = If the Overcloud kernel, initramfs, and QCOW2 image should be automatically downloaded and uploaded to Glance. Default: `false`.
* undercloud_config = Custom configurations for the Undercloud.

## Example Playbook

Simple:

```
---
- hosts: undercloud
  roles:
    - undercloud
```

Install the Undercloud and fully configure it:

```
---
- hosts: undercloud
  roles:
    - name: undercloud
      vars:
        tripleo_undercloud_install: true
        tripleo_undercloud_upload_images: true
```

## License

Apache v2.0

# ansible_role_undercloud

A role to configure and install the Undercloud as part of an OpenStack deployment using TripleO.

## Requirements

* Ansible >= 2.7

## Dependencies

None.

## Role Variables

* undercloud_install (boolean) = If the "openstack undercloud install" command should be executed.
* undercloud_upload_images (boolean) = If the Overcloud kernel, initramfs, and QCOW2 image should be automatically downloaded and uploaded to Glance.
* undercloud_config (dictionary) = Custom configurations for the Undercloud.
* undercloud_nameservers (string) = A comma-separated list of DNS resolvers.
* undercloud_ntp_servers (string) = A comma-separated list of NTP servers.

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

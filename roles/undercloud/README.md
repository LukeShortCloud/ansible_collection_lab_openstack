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
* undercloud_enable_cert (boolean) = Enable the generation of a self-signed certificate.
* undercloud_public_host (string) = The IP address or hostname that the certificate should bind to.
* undercloud_masquerade (boolean) = Enable masquerading on the control plan (provisioning) network.

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
        undercloud_install: true
        undercloud_upload_images: true
        undercloud_nameservers: "8.8.8.8,8.4.4.8"
        undercloud_ntp_servers: "0.pool.ntp.org,1.pool.ntp.org,2.pool.ntp.org,3.pool.ntp.org"
```

## License

Apache v2.0

# tripleo_heat_templates (Ansible Role)

An Ansible role for generating TripleO Heat templates for deployment.

## Requirements

* Ansible >= 2.9

## Role Variables

* tht_save_dir (string) = The directory to save the templates to.
* tht_release (string) = The OpenStack release to target. `queens` or `train`.
* tht_roles_data_minimal (boolean) = Generate a minimal roles_data.yml file.
* tht_roles_data_storage (boolean) = Enable storage related roles.
* tht_predeployed (boolean) = Generate predeployed server template.
* tht_controller_nodes (dictionary) = A list of dictionaries describing the `hostname` and `address` to be used for predeployed nodes.
* tht_compute_nodes (dictionary)
* tht_dns_servers (list) = A list of DNS servers to use for the Overcloud.
* tht_ntp_servers (list) = A list of NTP servers to use for the Overcloud.
* tht_low_memory (boolean) = Enable the low-memory-usage environment file.
* tht_ctlplane_network_cidr (string) = The full network CIDR for the control plane.
* tht_distro (string) = The EL distribution the templates should be generated for. `centos` or `rhel`.
* tht_swap (boolean) = If swap should be created and enabled.
* tht_swap_size (string) = The size (in MiB) of swap to create.
* tht_config_download (boolean) = For Queens only, if the deployment should use Ansible/config-download instead of Heat.
* tht_ssh_user (string) = The Overcloud SSH user to use for the initial deployment.
* tht_ssh_key (string) = The path to the Overcloud SSH private key to use for the initial deployment.

## Dependencies

None.

## Example Playbook

```
---
- hosts: localhost
  gather_facts: false
  roles:
    - name: tripleo_heat_templates
      vars:
        tht_controller_nodes:
          - hostname: controller0
            address: 192.168.24.111
        tht_compute_nodes:
          - hostname: compute0
            address: 192.168.24.121
```

The provided `net-config-nic1-public-nic2-ctlplane-{queens,train}.yaml` templates provide a similar layout of the Undercloud network configuration for the Overcloud. `nic1/eth0` is the public facing interface (for floating IPs) and `nic2/eth1` is the private interface (for internal Undercloud and Overcloud service communication). The default gateway is set to the Undercloud server `192.168.24.1` which should be setup with for to do masquerading/NAT.

## License

Apache

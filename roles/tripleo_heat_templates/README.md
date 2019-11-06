# tripleo_heat_templates (Ansible Role)

An Ansible role for generating TripleO Heat templates for deployment.

## Requirements

None.

## Role Variables

- tht_save_dir = The directory to save the templates to. Default: `/tmp/tht_custom`.
- tht_release = The OpenStack release to target. `queens` or `train`. Default: `queens`.
- tht_roles_data_minimal = Generate a minimal roles_data.yml file. Default: `true`.
- tht_roles_data_storage = Enable storage related roles. Default: `true`.
- tht_predeployed = Generate predeployed server template. Default: `true`.
- tht_controller_nodes = A list of dictionaries describing the `hostname` and `address` to be used for predeployed nodes.
- tht_compute_nodes
- tht_dns_servers = A list of DNS servers to use for the Overcloud.
- tht_ntp_servers = A list of NTP servers to use for the Overcloud.

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

## License

Apache

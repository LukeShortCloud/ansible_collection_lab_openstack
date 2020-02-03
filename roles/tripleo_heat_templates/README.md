# tripleo_heat_templates (Ansible Role)

An Ansible role for generating TripleO Heat templates for deployment.

## Requirements

None.

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

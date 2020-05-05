# Ansible Role: el_repo_version

Pin CentOS to a specific minor release hosted on the CentOS Vault.

## Requirements

- Ansible 2.8

## Role Variables

- el_repo_version (string) = The minor version of CentOS (7.Y) to pin the repositories to. Only older versions hosted on [vault.centos.org](http://vault.centos.org/) are supported.
    - CentOS 7:
        - C7.0.1406
        - C7.1.1503
        - C7.2.1511
        - C7.3.1611
        - C7.4.1708
        - C7.5.1804
        - C7.6.1810
        - C7.7.1908

## Dependencies

None.

## Example Playbook

```
---
- hosts: centos7
  roles:
    - name: el_repo_version
      vars:
        el_repo_version: C7.7.1908
```

## License

Apache v2.0

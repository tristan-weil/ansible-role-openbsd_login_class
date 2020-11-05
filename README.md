# Ansible Role: OpenBSD_login_class

An Ansible Role that allows to configure a login class on OpenBSD.

[![Actions Status](https://github.com/tristan-weil/ansible-role-openbsd_login_class/workflows/molecule/badge.svg?branch=master)](https://github.com/tristan-weil/ansible-role-openbsd_login_class/actions)

## Role Variables

Available variables are listed below, (see also `defaults/main.yml`).

See https://man.openbsd.org/login.conf.5 for more information.

Mandatory variables:

| Variable      | Description |
| :------------ | :---------- |

Optional variables:

| Variable      | Default | Description |
| :------------ | :------ | :---------- |
| openbsd_login_class_capdb | False | *True / False*: enable the building of the /etc/login.db file
| openbsd_login_classes | [] | a list of <*login class*>

### <*login class*>

A *login_class* represents a new entry in the /etc/login.conf file.

Mandatory variables:

| Variable      | Description |
| :------------ | :---------- |
| name          | the name of the class |

Optional variables:

| Variable      | Default | Description |
| :------------ | :------ | :---------- |
| state         | present | *present / absent*: to add or remove the class |
| services      | []      | a list of services to restart |
| capabilities  | []      | a list of <*capability*> |

### <*capability*>

A *capability* represents a capability.

Mandatory variables:

| Variable      | Description |
| :------------ | :---------- |
| name          | the name of the capability |
| value         | the value of the capability |

Optional variables:

| Variable      | Default | Description |
| :------------ | :------ | :---------- |

## Example Playbook

    - hosts: 'webservers'
      roles:
        - role: 'OpenBSD_login_class'
          name: 'elasticsearch'

          service:
            name: 'elasticsearch'
            restart: True
        
          capabilities:
          - name: 'openfiles'
            value: 65536
          - name: 'tc'
            value: daemon
            
## Todo

None.

## Dependencies

None.

## Supported platforms

See [meta/main.yml](https://github.com/tristan-weil/ansible-role-openbsd_login_class/blob/master/meta/main.yml)

## License

See [LICENSE.md](LICENSE.md)

# Ansible Role: OpenBSD_login_class

An Ansible Role that allows to configure a login class on OpenBSD.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    name:                       # name of the login class
    
The `name` of the class must be provided.
          
    capabilities: []
      - name:
        value:

The `capabilities` are listed here.
Each item must include the `name` of the capability and its `value`.
    
    service: [optional]        # service configuration                    
      name:
      restart:
      
If the login class of a service is modifier, it is possible to restart the service by enabling these variables.

See https://man.openbsd.org/login.conf.5 for more information.

## Dependencies

None.

## Example Playbook

    - hosts: webservers
      roles:
        - role: OpenBSD_login_class
          name: elasticsearch

          service:
            name: elasticsearch
            restart: True
        
          capabilities:
          - name: openfiles
            value: 65536
          - name: tc
            value: daemon
            
## Todo

None.

## License

```
Copyright (c) 2018 Tristan Weil <titou@lab.t18s.fr>

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

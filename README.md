# Ansible CIS repository role

This is an [Ansible](http://www.ansible.com) role to send mails.

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - role: amtega.mail
      vars:
        mail_defaults:
          charset: utf-8
          from: my@acme.com
          host: smtp.acme.com
          password: mypassword
          port: 587
          secure: starttls          
          subtype: plain
          timeout: 20          
          username: my

        mail_messages:
          - attach: /path/onefile
            bcc: bcc@acme.com
            body: This is testing message 1
            cc: cc@acme.com        
            subject: Testing message 1
            to: you@acme.com

          - attach: /path/anotherfile
            bcc: bcc@acme.com
            body: This is testing message 2
            cc: cc@acme.com        
            subject: Testing message 2
            to: you@acme.com            
```

## Testing

Tests are based on [molecule with docker containers](https://molecule.readthedocs.io/en/latest/installation.html).

To run the tests you have to pass the following variables:

- `ANSIBLE_INVENTORY`: path to an inventory providing the variables required by the role
- `ANSIBLE_VAULT_PASSWORD_FILE`: path to the file containing the vault password required for the previous inventory (optional)

```shell
cd amtega.mail

ANSIBLE_INVENTORY=~/myinventory ANSIBLE_VAULT_PASSWORD_FILE=~/myvaultpassword
molecule test
```

## License

Copyright (C) 2022 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Juan Antonio Valiño García.

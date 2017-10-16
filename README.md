# Ansible Role: zeyple

[![Build Status](https://img.shields.io/travis/mimacom/ansible-role-zeyple.svg)](https://travis-ci.org/mimacom/ansible-role-zeyple)

Installs zeyple as a content filter module for postfix. Zeyple is a python
script which receives outgoing mails from postfix. For each recipient, a
matching (local) PGP key is searched, and if found, the mail is being encrypted.
Afterwards, the mail is re-injected into postfix for further processing (i.e.
send to a mail relay or to the destination mail server).

This process is transparent to the sending user. The receiving user must have
the corresponding PGP private key to decrypt the message. For more information
about zeyple, visit the [project page](https://github.com/infertux/zeyple).

This role is tested on CentOS 7.

## Requirements

None, but it's recommended to have postfix already installed and configured.
Otherwise, postfix will be installed using the default configuration.

## Role Variables

    # Specify zeyple version to install
    zeyple_version: 1.2.0


## Dependencies

None.

## Example Playbook

    - hosts: servers
      become: yes
      roles:
        - role: mimacom.zeyple
          zeyple_version: 1.2.0

## License

Apache License 2.0

## Author Information

This role was created by [Remo Wenger](http://www.remowenger.ch).

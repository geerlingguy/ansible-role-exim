# Ansible Role: Exim

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-exim.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-exim)

Installs Exim (a Mail Transfer Agent) on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    exim_dc_eximconfig_configtype: internet

(Debian/Ubuntu only) Main configuration type. Should be 'internet' for public mail sending, or 'local' if mail should only be delivered locally. See Exim documentation for other options.

    exim_dc_localdelivery: mail_spool

(Debian/Ubuntu only) Default transport for local mail delivery. Defaults to `mail_spool` if unset.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
        - { role: geerlingguy.exim }

## License

MIT / BSD

## Author Information

This role was created in 2015 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).

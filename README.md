# Ansible Role: Exim

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-exim.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-exim)

Installs Exim (a Mail Transfer Agent) on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    exim_dc_eximconfig_configtype: internet

Mail configuration type. Should be one of:

  - 'internet' for public mail facing server,
  - 'smarthost' for relay via smarthost, but accept via SMTP,
  - 'satellite' if sending via smarthost (c.f. 'exim_dc_smarthost'), or
  - 'local' if mail should only be delivered locally.

See Exim documentation for other options.  *(Debian/Ubuntu only)*

    exim_dc_other_hostnames: "{{ansible_hostname}}"

Other hostnames for which this host will accept email.  *(Debian/Ubuntu only)*

    exim_dc_smarthost: ''

Relay mail through a different "smarthost" (or for 'satellite')  *(Debian/Ubuntu only)*

    exim_dc_readhost: ''

Rewrite outgoing mail local machine with this value.  *(Debian/Ubuntu only)*

    exim_dc_hide_mailname: ''

Hide the local mailname in the headers of outgoing messages (or not).  *(Debian/Ubuntu only)*

    exim_dc_localdelivery: mail_spool

Local delivery method.  *(Debian/Ubuntu only)*

    exim_primary_hostname: ""

Force a primary server hostname for Exim. Usually you don't need to set this, but if Exim can't reliably determine the FQDN of your server, you can set this and it will ensure Exim uses the correct hostname.  If empty, the directive will be ignored.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
      - role: geerlingguy.exim
        vars:
          exim_dc_eximconfig_configtype: satellite
          exim_dc_readhost: 'domain.org'
          exim_dc_smarthost: 'mail.domain.org'
          exim_dc_hide_mailname: 'true'

## License

MIT / BSD

## Author Information

This role was created in 2015 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).

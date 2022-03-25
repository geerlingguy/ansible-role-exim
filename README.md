# Ansible Role: Exim

[![CI](https://github.com/geerlingguy/ansible-role-exim/workflows/CI/badge.svg?event=push)](https://github.com/geerlingguy/ansible-role-exim/actions?query=workflow%3ACI)

Installs Exim (a Mail Transfer Agent) on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    exim_primary_hostname: ""

Force a primary server hostname for Exim. Usually you don't need to set this, but if Exim can't reliably determine the FQDN of your server, you can set this and it will ensure Exim uses the correct hostname.

### Debian/Ubuntu only

These variables are only for Debian/Ubuntu. See [man 8 update-exim4.conf](https://manpages.debian.org/bullseye/exim4-config/update-exim4.conf.8.en.html#CONFIGURATION_VARIABLES) for more information.

    exim_dc_eximconfig_configtype: internet

Main configuration type. Should be 'internet' for public mail sending, or 'local' if mail should only be delivered locally. See Exim documentation for other options.

    exim_dc_local_interfaces: "127.0.0.1 ; ::1"

List of IP addresses the Exim daemon should listen on. If this is left empty, Exim listens on all interfaces. Defaults to `127.0.0.1 ; ::1` if unset.

    exim_dc_relay_nets: ""

A list of machines for which we serve as smarthost. Please note that 127.0.0.1 and ::1 are always permitted to relay.

    exim_dc_localdelivery: mail_spool

Default transport for local mail delivery. Defaults to `mail_spool` if unset.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
        - geerlingguy.exim

## License

MIT / BSD

## Author Information

This role was created in 2015 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).

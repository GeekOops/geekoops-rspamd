[![Test deployment](https://github.com/GeekOops/geekoops-rspamd/actions/workflows/CI.yml/badge.svg)](https://github.com/GeekOops/geekoops-rspamd/actions/workflows/CI.yml)

# ansible role for setting up rspamd and unbond

Configurable ansible role for setting up unbound asa a recursive caching DNS resolver and rspamd.
Works with

- openSUSE Leap 15.4 -> tested

## Role Variables
--------------

You can set the following variables to configure the role. Here listed are the variables and their default settings.

Firewall configuration (disable by default)


| Value | Description | Default |
|-------|-------------|---------|
|`unbound_nameservers` | Nameservers to ask | "45.11.45.11 # DNS.SB" |


## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: jellyfish
      roles:
         - { role: geekoops-clamav, fangfrisch_prefix="/opt/fangfrisch" }

An advanced example for the imaginary `jellyfish` test server

    - hosts: jellyfish
      roles:
         - role: geekoops-clamav
           vars:
             fangfrisch_prefix: "/opt/fangfrisch"

## License

MIT

# Development

## Add githooks

This repository ships pre-commit git hooks that will check the yaml syntax. To configure them do

    git config --local core.hooksPath .githooks/

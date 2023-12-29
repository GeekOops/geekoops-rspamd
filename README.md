[![Test deployment](https://github.com/GeekOops/geekoops-rspamd/actions/workflows/CI.yml/badge.svg)](https://github.com/GeekOops/geekoops-rspamd/actions/workflows/CI.yml)

# ansible role for setting up rspamd and unbound

Configurable ansible role for setting up unbound as a recursive caching DNS resolver and rspamd.
rspamd triggers:

- virus check with clamav
- spam detection
- dkim signing

Works with

- openSUSE Leap 15.4 -> tested

## Role Variables
--------------

You can set the following variables to configure the role. Here listed are the variables and their default settings.

Firewall configuration (disable by default)


| Value | Description | Default |
|-------|-------------|---------|
|`unbound_nameservers` | Nameservers to ask | "45.11.45.11 # DNS.SB" |
|`rspamd_redis_connection`| rspamd redis socket |  "/var/run/redis/rspamd.sock" |
|`rspamd_password` | password for the rspamd web interface | "Q1" |
|`rspamd_dkim_key_length` | bit length of the rspamd dkim key| 2048 |
|`rspamd_dkim_key_selector`| selector for the DKIM key | 2023 |

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: jellyfish
      roles:
         - { role: geekoops-rspamd, rspamd_dkim_key_length="2048" }

An advanced example for the imaginary `jellyfish` test server

    - hosts: jellyfish
      roles:
         - role: geekoops-rspamd
           vars:
             rspamd_dkim_key_length: "2048"

## License

MIT

# Development
Some links:
- https://thomas-leister.de/mailserver-debian-buster/
- https://github.com/chkpnt/chkpnt-mailserver

# Notes
rspamc learn_ham always failed for me even as root user. 
Specifying secure_ip = "<my public IP>" in /etc/rspamd/local.d/worker-controller.inc made it work in dovecot.
A source for training data is here: https://spamassassin.apache.org/old/publiccorpus/ Note that currently rspamd needs 200 mails to start.

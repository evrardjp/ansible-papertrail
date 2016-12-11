Ansible Papertrail Role
=======================

[![Build Status](https://travis-ci.org/evrardjp/ansible-papertrail.svg?branch=master)](https://travis-ci.org/evrardjp/ansible-papertrail)

Role for configuring papertrail service.
Currently only rsyslog is supported.
Confirmed to be working on Debian and Redhat like.

Requirements
-------------------

- `papertrail_destination` must be configured


Role Variables
--------------

Mandatory:
- `papertrail_destination`

Not editable:
- `papertrail_rsyslog_packages`: name of the rsyslog packages required for your distribution.
- `papertrail_rsyslog_tls_packages`: name of the tls packages required for your distribution.
- `papertrail_rsyslog_service`: name of the rsyslog service under your distribution.
- `papertrail_ca_url`: Static variable to the CA download url. Used when `papertrail_enable_tls` is set to `True`.
- `papertrail_ca_checksum`: Static variable holding the checksum of the ca file. Used when `papertrail_enable_tls` is set to `True`.

Editable:
- `papertrail_logforwarder`: The forwarder used in papertrail. Only rsyslog is supported right now.
- `papertrail_enable_tls`: Switch this to `True` to enable tcp+tls log forwarding. Default is UDP usage.
- `papertrail_enable_tcp`: If you switch this to `True`, the log forwarding will be done in TCP instead of UDP. No TLS used in that case.
- `papertrail_loglevel`
- `papertrail_rsyslog_config`: This is a list of name+value items that are inserted in the rsyslog configuration.


Defaults
-----------

- `papertrail_logforwarder` is set to "rsyslog"
- `papertrail_enable_tls` and `papertrail_enable_tcp` are disabled by default.
- Switching `papertrail_enable_tls` to true will magically turn `papertrail_enable_tcp`, unless explicitly told not to (don't do that!).
- `papertrail_loglevel` default is `*.*` (send everything)
- `papertrail_rsyslog_config` has sane defaults defined, please check defaults/main.yml


Example Playbook
------------------------

    - hosts: all
      roles:
         - { role: evrardjp.papertrail, papertrail_destination: logs1234.papertrailapp.com:1234}


Next steps
----------

Add support for

- syslog-ng
- remote_syslog2
- other OSs

License
----------

Apache2

Author Information
-------------------------

Jean-Philippe Evrard

Ansible Papertrail Role
==============

Role for configuring papertrail service.
Currently only rsyslog is supported.
Confirmed to be working on Debian like systems

Requirements
-------------------

- `papertrail_destination` must be configured


Role Variables
--------------

Mandatory:
- `papertrail_destination`

Not editable:
- `papertrail_rsyslog_packages`
- `papertrail_rsyslog_tls_packages`
- `papertrail_rsyslog_service`

Editable:
- `papertrail_logforwarder`
- `papertrail_enable_tls`
- `papertrail_enable_tcp`
- `papertrail_loglevel`
- `papertrail_rsyslog_config`


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

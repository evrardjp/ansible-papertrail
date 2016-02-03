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



Defaults
-----------


Example Playbook
------------------------

    - hosts: all
      roles:
         - { role: evrardjp.papertrail, papertrail_destination: logs1234.papertrailapp.com:1234}


TODO
--------

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

Ansible role for a Mailserver
=============================

Ansible role to create a Mailserver on OpenBSD (>6.0) with OpenSMTPD, Dovecot, DKIMProxy and Rspamd.

Requirements
------------

OpenBSD, Python 2.7 (on client machine) and 10 minutes.

Notes
-----

This is still a WIP, so far, you need to create DKIM keys, new users and DNS entrys. Also, you need
to enable dovecot, smtpd, rspamd and dkimproxy_{in,out} at boot.

Feedback is welcome.

Example Playbook
----------------
```
---
- hosts: test
  roles:
     - role: gonzalo-.mailserver
  become: yes
  become_method: doas

  vars:
   domain: 'foobar.com'
   mail_dir: '/var/vmail'
   mail_user: 'gonzalo'
   release: '6.1'
   arch: 'amd64'
   installurl_mirror: 'https://ftp5.usa.openbsd.org/pub/OpenBSD/'
   pkg_path: 'https://ftp5.usa.openbsd.org/pub/OpenBSD/{{ release }}/packages/{{ arch }}/'
   packages_list:
    - dovecot
    - dovecot-pigeonhole
    - dkimproxy
    - rspamd
    - opensmtpd-extras
```

License
-------

BSD

Author Information
------------------

https://x61.sh/

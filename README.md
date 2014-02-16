Hardening
=====

This role installs and configures the following packages to harden your system:

 - fail2ban
 - logwatch
 - unattended-upgrades
 - chkrootkit
 - lynis

It creates a service user with full sudo rights.
Logwatch will send weekly mails but it is still up to you to configure your mailserver to be able to send mails.

It currently only provides this for Debian and Ubuntu. Nothing will happen when you run this rule on other systems.

Requirements
------------

This role requires Ansible 1.4 or higher and platform requirements are listed in the metadata file. The user that executes this script is expected to have ssh-keys generated on the management machine. 

**Note:** Since this role requires you to restart ssh it is best used alone or at least as the last playbook executed. Also ssh with password login is no longer possible, you need to have ssh-keys properly set up. If you make a mistake, you cannot access your server via ssh any more, so make sure you have an alternative access to debug problems.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	hardening_user:
	  id: username                   # new user account that gets created
	  password: password             # password to be used
	  shell: user shell              # the user shell to use
	hardening_admin_email: admin@example.org # where to send logwatch emails
	hardening_strong_ciphers: whether to only allow very string ciphers.

You might not want to use only strong ciphers if you use other clients than openssh to connect to the servers.
Examples include vzmigrate, and paramiko which is used by fabric. These programs would not be able to connect to the server if only the strongest ciphers are active.

Examples
========

Set up on all hosts

	- hosts: all
	  sudo: True
	  roles:
	     - { role: role-hardening}
	  vars:
	    hardening_user:
	      id: myuser
	      password: pwd
	      shell: /bin/bash
	    hardening_admin_email: myuser@example.com


Dependencies
------------

None

License
-------

BSD

Author Information
------------------

Stephan Hochhaus <stephan@yauh.de>

[yauh.de](http://yauh.de)



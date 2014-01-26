Hardening
=====

This role performs several tasks to secure a server on the internet.

Requirements
------------

This role requires Ansible 1.4 or higher and platform requirements are listed in the metadata file. The user that executes this script is expected to have ssh-keys generated on the management machine. 

**Note:** Since this role requires you to restart ssh it is best used alone or at least as the last playbook executed. Also ssh with password is no longer possible, you need to have ssh-keys properly set up.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	hardening:
	  user: username                 # new user account that gets created
	  password: password             # password to be used
	  admin_email: admin@example.org # where to send logwatch emails

Examples
========

Set up on all hosts

	- hosts: all
	  sudo: True
	  roles:
	     - { role: role-hardening, tags: secure}


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



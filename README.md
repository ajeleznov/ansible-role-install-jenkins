Role Name: ajeleznov.install-jenkins
Version:   1.0-SNAPSHOT
=========
Status: NOT RELEASED YET

This Ansible role installs the Jenkins automation server
on Redhat Family Linux (RedHat, CentOS) using RPM package file.

This role consists of several phases/steps that can be disabled using
corresponding flags (boolean variables):

Phases:


Requirements
------------

The target system is RPM-based Linux platform like Redhat or CentOS with
pre-installed java binaries. You can use for example a role ajeleznov.oracle-jdk
to install Oracle JDK on your system.

The Jenkins automation server will be installed on a dedicated disk partition,
mounted to a specific mount point like for example /j01 or /data.

Role Variables
--------------

See defaults/main.yml


Dependencies
------------

see Requirements

Example Playbook
----------------
```
hosts:		test
gather_facts:   False

tasks:
	- import_role:
	    name: ajeleznov.install-jenkins
	  vars:
      - TO_BE_DEFINED
```

License
-------

Apache v.2.0

Author Information
------------------

Dr. Andrei Jeleznov <mailto:andrei.jeleznov@kuehne-nagel.com>
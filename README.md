Role Name: ajeleznov.install-jenkins
=========
Version:   1.0-SNAPSHOT

This Ansible role installs the Jenkins automation server
on Redhat Family Linux (RedHat, CentOS) using RPM package file.

The path to the Jenkins home directory consists of the following parts:
mount_point - a mount point for a dedicated partition, owned by root
base_dir - a basis directory for any Jenkins installations, owned by jenkins user
jenkins_home - home directory for a jenkins installation

This role consists of several phases/steps that can be disabled using
corresponding flags (boolean variables):

Phases:
1. PREREQUISITES: Check for role prerequisites, it can not be skipped
2. JENKINS-REMOVE: Remove the existing Jenkins installation
3. JENKINS-INSTALL-RPM: Install Jenkins rpm package from stable jenkins redhat repository
4. JENKINS-EDIT-SYSCONFIG: Edit Jenkins config file to customize the installation layout
5. JENKINS-PREPARE-HOME: Do some initial System configuration through xml files
6. INSTALL-PLUGINS: Install list of selected Jenkins plugins
7. JENKINS-START: Start the Jenkins instance

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
- name:                               install-jenkins-playbook
  tags:                               [ "install-jenkins" ]
  hosts:                              [ test-host ]
  gather_facts:                       True
  become:                             True

  tasks:
  - import_role:
      name:                            "ajeleznov.install-jenkins"
    vars:
      jenkins_domain:                  "mydomain.kn"
      jenkins_memory_options:          "-Xms10g -Xmx30g"
```

License
-------

Apache v.2.0

Author Information
------------------

Dr. Andrei Jeleznov <mailto:andrei.jeleznov@kuehne-nagel.com>
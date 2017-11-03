cassandra_node
=========

A role that manages a Cassandra node on the target host.

Requirements
------------
N/A

Role Variables
--------------

The following variables are available in this role:


* `cassandra_tgz_src`: A URL pointed to a mirror of a tgz file for the desired Cassandra version.
* `jdk_version`: The package version to use when installing openjdk-1.8.0.

Dependencies
------------
N/A

Example Playbook
----------------

This role is intended to be used in conjunction with the `ec2_setup` role, however a simple use case is:

    - hosts: ec2_instances
      tasks:
        - include_role:
          name: cassandra_node

License
-------

MIT

Author Information
------------------

Richard Hofman
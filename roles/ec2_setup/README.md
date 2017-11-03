ec2_setup
=========

A role to provision a simple cluster of EC2 instances, with a common security group and keypair.

Requirements
------------

* boto
* boto3

Role Variables
--------------
The role uses the following variables internally for configuration:

  instance_params:
    instance_type: t2.micro
    ami_id: ami-ccecf5af
    number_instances: "{{ desired_instances }}"
    number_seeds: "{{ desired_seeds }}"
    keypair: ansible_prov_key

* `instance_type`: EC2 instance type to use for all members of the cluster.
* `ami_id`: ID of the AMI to use for all members of the cluster.
* `number_instances`: number of EC2 instances required.
* `number_seeds`: number of EC2 instances to set aside for Cassandra seed nodes.
* `keypair`: name of keypair to use. If set to `ansible_prov_key`, the role will create a new provisioning keypair and write the private key in `private/`.

Externally, the following two variables can be directly specified and map as described:

* `desired_instances` => `instance_params.number_instances`
* `desired_seeds` => `instance_params.number_seeds`

Dependencies
------------
N/A

Example Playbook
----------------

    - hosts: servers
      tasks:
        - include_role:
            name: ec2_setup
          vars:
            desired_instances: 3
            desired_seeds: 2

License
-------

MIT

Author Information
------------------

Richard Hofman
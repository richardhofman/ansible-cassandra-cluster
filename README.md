# Ansible: Cassandra Cluster Provisioning
## Overview
This repository contains a simple Ansible playbook, which provisions a single-datacentre, single-region
cluster of Cassandra nodes in AWS.

The playbook is capable of handling:

* Provisioning of a VPC security group
  - In the future, support for provisioning a full VPC and VPN gateway could significantly enhance the usefulness of this playbook.
* Provisioning of EC2 instances (associated with the generated security group)
  - Use `number_instances` to set the number (N) of EC2 instances to be created.
  - Use `number_seeds` to set number of seed nodes.
  - Use `ec2_instance_type` to set the AWS instance type. Defaults to t2.micro (free-tier).
  - Use `ami_id` to specify the API to base the EC2 instances off. This must be a RHEL7.x-based distro at this time.
* Installation and configuration of Cassandra:
  - Configuration of an N-node cluster, with K seed nodes (as previously mentioned).
  
## Usage

### Requirements
All plays will require the local machine (running the playbook) to meet the following requirements:

* boto
* boto3
* python >= 2.6

### Provisioning
1. Clone this repository: ``git clone https://github.com/richardhofman6/....``
2. Set desired configuration options in `vars.yml`.
3. Set environmental variables: `AWS_ACCESS_KEY` and `AWS_SECRET_KEY`.
4. Run: `AWS_ACCESS_KEY=X AWS_SECRET_KEY=Y ansible provision_cass_cluster.yml`

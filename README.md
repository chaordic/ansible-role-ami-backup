ami-backup
=========

A simple role to backup [AMI](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html) from AWS EC2.

Requirements
------------

ansible>2.1
boto>2.39

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    ami_backup_count: 5

Deletes the oldest number of AMI's that exceed the specified count.

    ami_backup_remove: yes

Delete oldest number of AMI's after AMI creation.

    ami_backup_ec2_id: AMI_ID

The EC2 Instance ID required to backup AMI.

    ami_backup_ec2_region: us-east-1

The EC2 region where the instance is hosted.

    ami_backup_ec2_name: myec2instance

EC2 Tag name used to identify the instance. Tag name must exist for backup.

    ami_backup_tags_product: myproduct
    ami_backup_tags_role: myproduct-backup
    ami_backup_tags_team: operations

AMI Tagging.

Example Playbook
----------------
- hosts: servers
  vars:
    # ami_backup vars
    ami_backup_count: 10
    ami_backup_remove: yes
    # ami_backup_ec2
    ami_backup_ec2_id: i-d5e29291
    ami_backup_ec2_region: us-east-1
    ami_backup_ec2_name: myec2instance
    # ami_backup_tags
    ami_backup_tags_product: myproduct
    ami_backup_tags_role: myproduct-backup
    ami_backup_tags_team: operations

  roles:
     - role: chaordic.ami-backup

License
-------

GPLv3

Author Information
------------------

Cloud Operations Team, SRE. Linx+Neemu+Chaordic

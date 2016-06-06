Ansible-OVB
===========

Ansible roles for deploying TripleO heat stack on existing OpenStack cloud using ``OpenStack Virtual Baremetal`` project

Requirments
-----------

All the packages needed for running ansible-ovb are listed in requirements.txt

To install the packages, run ``pip install -r requirements.txt``

Usage
-----

Deploy TripleO stack
^^^^^^^^^^^^^^^^^^^^

#. Edit ansible-ovb.cfg with your cloud details and custom deployment parameters::

       vi ansible-ovb.cfg

       username: <cloud_username>
       password: <user_password>
       tenant_name: <project_name>
       auth_url: <cloud_auth_url> # For example http://190.20.42.60:5000/v2.0
       key_name: <keypair_name>
       key_file: <key_file_path>

       prefix: <resources_prefix> # prefix string for provisioned resources
       image: <image for bm nodes> # For example rhel-guest-image-7.2-20151102.0
       flavor: <nodes flavor> # For example m1.large
       overcloud_nodes_count: 2 # The number of overcloud nodes to provision

#. Deploy OVB-based TripleO setup::

       ansible-playbook -i hosts playbooks/deploy.yaml -e @ansible-ovb.cfg

Cleanup TripleO stack
^^^^^^^^^^^^^^^^^^^^^

#. Use the following command to remove existing stack::

       ansible-playbook -i hosts playbooks/cleanup.yaml -e @ansible-ovb.cfg

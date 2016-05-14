Ansible-OVB
===========================

Ansible role for deploying TripleO heat stack on existing OpenStack cloud using ``OpenStack Virtual Baremetal`` project

Requirments
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

All the packages needed for running ansible-ovb are listed in requirements.txt

To install them, run ``pip install -r requirements.txt``

Usage
------

#. Edit ansible-ovb.cfg with your cloud details and custom deployment parameters

   vi ansible-ovb.cfg

   username: my_username
   password: 123456
   tenant_name: my_project/tenant_name
   auth_url: http://X.X.X.X:5000/v2.0
   key_name: keypair_name
   prefix: test-
   image: rhel-guest-image-7.2-20151102.0
   flavor: m1.large

#. Run!

   ansible-playbook -i hosts playbooks/deploy.yaml -e @ansible-ovb.cfg

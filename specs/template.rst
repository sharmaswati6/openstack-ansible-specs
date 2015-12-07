Designate deployment using openstack-ansible playbooks
######################################################
:date: 2015-12-07 13:30
:tags: designate,openstack-ansible

The purpose of this spec is to add support for the OpenStack Designate program
to OpenStack Ansible, allowing the deployment of Designate along with the
core openstack components using ansible-playbooks.

Blueprint - Designate deployment on openstack-ansible:
     
https://blueprints.launchpad.net/openstack-ansible/+spec/designate-for-openstack-ansible
        
Problem description
===================

Presently, while deploying openstack on ansible-playbooks only the core
openstack components get deployed. The deployment of other components eg,
designate,trove on playbooks is not supported yet. To use other component's
services, one requires to understand the whole playbook architecture along
with openstack deployment and then deploy the component manually.   


Proposed change
===============

The proposed changes include:

     Creation of an openstack-ansible-designate repository and ansible role to
     support the deployment of Designate.
     Tests to verify the new ansible role.


Alternatives
------------

None


Playbook/Role impact
--------------------

Test playbooks will be placed in the openstack-ansible-designate repository
for functional testing purposes, with no initially proposed changes to
openstack-ansible playbooks.

In the future, once the desigante role is found to be useful and acceptable,
a future spec will address the integration of the designate role with the
main openstack-ansible repository.


Upgrade impact
--------------

None


Security impact
---------------

None


Performance impact
------------------

None


End user impact
---------------

Deployers will be able to deploy designate and use DNSaaS through
openstack-ansible.


Deployer impact
---------------

Designate specific configuration options will be added to the new repository.
When support for the new Designate role is added to the parent repository,
new config options will be made available. However it is expected that 
Designate support will initially be disabled, requiring that deployers 
explicitly enable Designate support, and to enroll hosts for openstack-ansible
to use.


Developer impact
----------------

As this change is self-contained initially, no impact on other developers is
expected.


Dependencies
------------
None


Implementation
==============

Assignee(s)
-----------

Primary assignee:
  Swati Sharma ( IRC: Swati)

Other contributors:
  None


Work items
----------

Ask for the new repository, openstack-ansible-desigante, to be created.
Create the role for desigante support
  Add support for running designate-api, designate-cental, 
  designate-pool_manager, designate-sink, designate-mdns
  Add support for including python-designateclient, which is the operator
  tool for supporting Designate.


Testing
=======

Testing has to be done. 
Develop a test playbook to deploy to hardware that can exercise the new role.
Develop tests that verify the role’s behaviour independent of actually 
requiring hardware to test the role’s functionality.


Documentation impact
====================

Adding support to the user guide on how to enable Designate support will be 
required.


References
==========

[1] The Designate server: http://git.openstack.org/cgit/openstack/designate/

[2] The Designate client: http://git.openstack.org/cgit/openstack/python-designateclient/


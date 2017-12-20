Usage
=====

These playbooks manage the lifecycle of virtual network functions in an OpenStack cloud environment via ansible in a standardized manner.

Access to cloud API endpoints is defined
via the "configurations/clouds.yml" file
which is encrypted via ansible-vault.

The playbooks take the name of VNF as a paramater/variable as shown in the examples below.

The VNF specific requirements are kept in
variables file which will be downloaded from a repository in the course of the process.

Prerequisites:
--------------

* ansible
* git
* clone this repoitory
* access to an OpenStack API endpoint (configurations are kept in clouds.yaml in the configurations sub-directory)
* a VNF descriptor stored at:

  https://raw.githubusercontent.com/BernardTsai/applications/master/{{vnf}}/descriptor.yml"

Inventory:
----------

Determine the current setup of a tenant:

    ansible-playbook inventory-playbook.yml  --vault-id passphrase.txt --extra-vars "vnf=Clearwater"

Deployment:
----------

Create/update a new tenant:

    ansible-playbook deployment-playbook.yml  --vault-id passphrase.txt --extra-vars "vnf=Clearwater"

Cleanup
----------

Destroy the virtual resources of an existing tenant (tenant and administrator will remain):

    ansible-playbook cleanup-playbook.yml  --vault-id passphrase.txt --extra-vars "vnf=Clearwater"

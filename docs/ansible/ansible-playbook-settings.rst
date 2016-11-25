Ansible playbook settings
=========================

If you don't use the UDF environment but your own, you may have to update a few settings in the playbook for the cluster deployment. 

.. warning::

	You need to do this kind of update if you plan to run the ansible playbook to setup a cluster. if standalone mode, it's not needed.

* **/etc/ansible/hosts** to specify the relevant nodes that the playbook has to setup 
* **ansible/playbooks/groups_var/slaves/slaves_variables** - The slaves directory load variable(s) that will be assigned to all the nodes in the group "slaves" (in your /etc/ansible/hosts file). You need to update this file to specify the relevant interfaces to your agents
* **ansible/playbooks/groups_var/masters/masters_variables** - the masters directory load variable(s) that will be assigned to all the nodes in the group "masters" (in your /etc/ansible/hosts file). You need to update this file to specify the relevant interfaces to your agents

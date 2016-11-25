Ansible playbook settings
=========================

If you don't use the UDF environment but your own, you may have to update a few settings in the playbook for the cluster deployment. 

.. warning::

	If you don't use the cluster blueprint, you'll need to update a few files to make it fit your environment depending on the environment. 


Here is the list of files to update: 

* **/etc/ansible/hosts** to specify the relevant nodes that the playbook has to setup - *this is already set properly in the UDF standalone and cluster deployment**

* **ansible/playbooks/groups_var/slaves/slaves_variables** - The slaves directory load variable(s) that will be assigned to all the nodes in the group "slaves" (in your /etc/ansible/hosts file). You need to update this file to specify the relevant interfaces to your agents. **This is not needed in the UDF standalone deployment and already setup properly in the UDF cluster deployment**

* **ansible/playbooks/groups_var/masters/masters_variables** - the masters directory load variable(s) that will be assigned to all the nodes in the group "masters" (in your /etc/ansible/hosts file). You need to update this file to specify the relevant interfaces to your agents. **You need to update this for the UDF blueprint deployment

Using Ansible with GCP
======================

Basic, no frills, single file playbooks to provision, run tasks and terminate a vm.

Ansible control machine is running Mac OS 10.15.1

ansible --version  = 2.9.0

[1]: https://docs.ansible.com/ansible/latest/scenario_guides/guide_gce.html
[2]: https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys

Prerequisites
-------------

* Necessary libraries have been installed on Ansible control machine. [Link][1]
* GCP Service Account credentials have been created and downloaded. See Ansible GCP Guide. [Link][1]
* GCP SSH Keypair has been created locally and the public key has been uploaded to the **GCP | Computer Engine | Metadata | SSH Keys**. Note that this will give project wide access to ssh to linux computer instances and may be undesired. In this case i'm using 'gce-user' and have an associated ssh keypair. (Keypair name is referenced in the playbook). [Link][2]

Notes
-----

* Default network is being used which already has the pre-populated firewall rules setup for remote access via ssh.


Provision a basic VM (Red Hat Enterprise Linux)
-----------------------------------------------

Playbook run-time : ~ 5 mins

This playbook will:

1. Launch an google compute engine rhel instance
2. Connect via ssh to the **external IP** of the new instance
3. Gather facts on the instance
4. Reboot the instance
5. Terminate the instance

* `<gcp_project>` ***value*** =  path to the GCP Service account
* `<gcp_cred_file>` ***value*** =  path to the GCP Service account credentials file. e.g ~/gcp_creds/cred_file.json
* `<ansible_ssh_private_key_file>` ***value*** = path to private key file. e.g ~/.ssh/my_key

>ansible-playbook launch_gcp_compute_rhel.yml --extra-vars '{"gcp_project":"***value***","gcp_cred_file":"***value***","ansible_ssh_private_key_file":"***value***" }'

Provision a basic VM (Windows Server 2016)
-----------------------------------------------

Coming soon....

ansible-bootstrap
=================

This is a simple Ansible role to prep a fresh node for management by ansible.
This primarily involves:

 * Configuring a known/common management user account
 * Having that user trust an OpenSSH public key
 * Granting password-less sudo access to the node
 * Ensuring that required packages (Python, sudo, etc) are installed

This role doesn't explicitly disable any default user account used to bootstrap
the node initially.

Requirements
------------

Requires a way to log into the remote node via ssh. This could be using a public
key with a passphrase, a common default username/password pair and potentially a
password for privilege escalation.

Role Variables
--------------

 * `orchestration_user` -- The user to be used to manage this node (eg, ansible).
 * `orchestration_pubkey` -- The contents of an OpenSSH public key file, or a URL to an OpenSSH public key.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: mattgeddes.ansible_bootstrap, orchestration_user: ansible, orchestration_pubkey: "http://keyserver.local/ansible.key" }

License
-------

Apache 2.0


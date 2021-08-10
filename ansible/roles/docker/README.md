Role Name
=========

Install docker on Ubuntu hosts

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values:

  # This are the pre-requisites packages that you need before install docker
  packages:
    - apt-transport-https
    - ca-certificates
    - linux-image-extra-virtual

  # non-sudo users that want to be able to run docker
  docker_users:
    - vagrant

Dependencies
------------

None.

Example Playbook
----------------

- hosts: servers
  roles:
    - docker

License
-------

BSD

Author Information
------------------

This role was created in 2016 by Claudiu Sonel.

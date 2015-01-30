template for starting an ansible project
=======================

####Setup

Requires [Vagrant](https://docs.vagrantup.com/v2/installation/) and [Ansible](http://docs.ansible.com/intro_installation.html)

Install ansible on Ubuntu

    $ sudo apt-get install software-properties-common
    $ sudo apt-add-repository ppa:ansible/ansible
    $ sudo apt-get update
    $ sudo apt-get install ansible

Install ansible on Mac

    $ brew install ansible

Install vagrant plugin cachier to cache repository packages

    $ vagrant plugin install vagrant-cachier

####Running in vagrant

    vagrant up
    bin/export_vagrant_ssh_keys
    bin/provision


####Destroying

    bin/destroy

####Running in production

Before running in production the hosts file will need to be copied to a file named production and then modified to fit your server. Afterwards you can run the production provisioning script. The production file is ignored by git for safety.

    bin/provision_production
    
####Ansible best practices

http://docs.ansible.com/playbooks_best_practices.html

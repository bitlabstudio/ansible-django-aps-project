# Ansible Playbook for django-aps-project

DO NOT USE THIS! WORK IN PROGRESS

This is an Ansible playbook that sets up a server to run
[django-aps-project](https://github.com/bitmazk/django-aps-project).

Using this playbook involves several steps:

* Setup your server with Ubuntu and create a new user `webuser`
* Change the variables of this playbook
* Run the playbook

# Prerequisites

## Setup webserver

Please install the following packages:

    sudo apt-get install make python-dev libpcre3 libpcre3-dev

## Change variables

Next, copy the `hosts.example` file and change the USERNAME to your Webfaction
account name.

    cp hosts.example hosts
    vim hosts

Similarly, copy the `vars/external_vars.yml` file and change all values to
your liking. The values you need to change are all uppercase letters.

    cd vars
    cp external_vars.yml.example external_vars.yml
    vim external_vars.yml

# Execute the playbook

Now execute the playbook:

    ansible-playbook -i hosts site.yml

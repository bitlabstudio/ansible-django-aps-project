Important
=========

This app has been discontinued and is no longer maintained.

# Ansible Playbook for django-aps-project

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

Make sure that a crontab exists:

    crontab -e
    # save and quit

You might also want to create a public SSH key for the server and add it to
it's own ``authorized_keys`` file.

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

# Create database

After the server provisioning, you need to connect to your database and create
a role ``aps_project`` and a database ``aps_project`` with the password that
you set as ``postgres_pw`` in ``external_vars.yml``.

# Deployments

When new code has been pushed to Github, a deployment can be done via:

    ansible-playbook -i hosts deploy_staging.yml
    ansible-playbook -i hosts deploy_production.yml

# Import database from production to staging

If you need to debug complex problems and need the production database on the
staging server, you can imort the database via:

    ansible-playbook -i hosts import_db.yml

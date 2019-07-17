# Ansible playbook for AiiDA Lab Server

This is an [ansible](https://www.ansible.com/overview/how-ansible-works) playbook for setting up a multi-user [AiiDA lab](https://aiidalab.materialscloud.org) 
either on a physical server or on a virtual machine (e.g. on Amazon Web Services or OpenStack).

### Prerequisites

### Server

- A server running Ubuntu 18.04 with open ports 22 (ssh), 80 (http) and 443 (https).
- passwordless ssh access to the server via ssh key

For instructions on how to set up cloud services, see [here](https://tljh.jupyter.org/en/latest/index.html).

### Your machine

- [bash](https://www.gnu.org/software/bash/)
- [python](https://www.python.org/)
- [git](https://git-scm.com/)

Instructions for the terminal:
```
git clone git@github.com:aiidalab/ansible-playbook-aiidalab.git
cd ansible-playbook-aiidalab
pip install -r requirements.txt
ansible-galaxy install -r requirements.yml
```

### Installation

1. select aws/os host in the `./hosts` file
1. Edit corresponding `./host_vars/*.yml` file and adapt path to SSH private key
1. run `ansible-playbook playbook.yml`

Once finished, navigate to the IP address of your server.

**Warning:** To keep things simple, this uses the [`FirstUseAuthenticator`](https://github.com/jupyterhub/firstuseauthenticator), which simply creates new JupyterHub users when they enter their username and password.
In order to disable the creation of new users, uncomment the corresponding lines in the [`playbook.yml`](playbook.yml).

## Connecting to authentication services

The `FirstUseAuthenticator` can be useful to get started but for production you may want to connect to an OAuth2 server for authentication.
See the [OAuthenticator](https://github.com/jupyterhub/oauthenticator) for instructions on how to connect to external authentication services.

## Acknowledgements

This work is supported by the [MARVEL National Centre for Competency in Research](http://nccr-marvel.ch) 
and the [MaX European centre of excellence](http://www.max-centre.eu/)

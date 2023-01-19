# Setup


## Install Ansible

```sh
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
ansible --version
```

## Clone the repository

```sh
git clone https://github.com/fabricesemti80/bind9-server.git
cd bind9-server
```

## (Optional) Disable DNS

The default DNS service of Ubuntu is interfers with Bind9, so we turn it off by running the relevant playbook.

```sh
ansible-playbook ansible/playbooks/prepare-for-bind.yml
```

## Install Docker and Docker-Compose

We obviously need these tools.

```sh
ansible-playbook ansible/playbooks/docker.yaml
```

## Docker-compose up

This should bring up the Bind9 dns server.
```sh
cd docker-compose/
docker-compose up
```

Note:

# Setup


# On bind host

- Create an ubuntu 20.04 container
- during creation add the ssh public key (this will be added to the `root` user)

# On management host

- use `ansible all -m ping -i inventories/hosts ` to test connectivity (update the inventory file if neccesary)
- install Docker and Docker Compose by running the relevant playbook

```sh
ansible-playbook -i inventories/hosts playbooks/docker.yaml

## sample output:

#PLAY [all] **************************************************************************************************************

#TASK [Gathering Facts] **************************************************************************************************
#ok: [bind9]

#TASK [install dependencies] *********************************************************************************************
#changed: [bind9] => (item=apt-transport-https)
#ok: [bind9] => (item=ca-certificates)

# ... output omited ...

#PLAY RECAP **************************************************************************************************************
#bind9                      : ok=10   changed=7    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0


```

- connect to the server and verify the isntallation with `docker version` and `docker-compose version`

- run the playbook to disable the built in dns of Ubuntu

```sh
ansible-playbook -i inventories/hosts playbooks/disable-dns.yaml
```

# ref

<https://medium.com/codex/how-to-install-docker-using-ansible-84d40005169>
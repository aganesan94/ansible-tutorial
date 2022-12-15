# Introduction 

## SSH-ing to a server via a SSH key Ping and Check if Targets exist
* Refer contents ssh-and-ping.txt

```shell
ansible ansible-target-1 -m ping -i ssh-and-ping.txt
ansible ansible-target-2 -m ping -i ssh-and-ping.txt
```

### Ansible configuration files
All ansible configuration files are stored in

```shell
/etc/ansible/ansible.cfg
```

## Fundamentals

### Inventory

Ansible automates tasks on managed nodes or “hosts” in your infrastructure, using a list or group of lists known as inventory.

```shell
/etc/ansible/hosts
```

* The default inventory can be picked up with the **-i** parameter
* Commonly used inventory parameters include
  * ansible_connection (ssh/winrm) - connection parameters for linux/windows
  * ansible_port - Port
  * ansible_user - Username
  * ansible_ssh_pass/ansible_password  - Password
  * ansible_ssh_private_key_file - Location of private key file
*  Creating a group or a group of groups
```shell
# Sample Inventory File

# Web Servers
web1 ansible_host=server1.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web2 ansible_host=server2.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web3 ansible_host=server3.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!

# Database Servers
db1 ansible_host=server4.company.com ansible_connection=winrm ansible_user=administrator ansible_password=Password123!


[web_servers]
web1
web2
web3

[db_servers]
db1

[all_servers:children]
web_servers
db_servers
```


### Playbook

* A single yaml file to discuss a list of tasks to be run on hosts

# Usecase-1
```shell
-
    name: 'Execute a date command on localhost'
    hosts: localhost
    tasks:
        -
            name: 'Execute a date command'
            command: date
```
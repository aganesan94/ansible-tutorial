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
  * ansible_connection - connection parameters
  * ansible_port - Port
  * ansible_user - Username
  * ansible_ssh_pass  - Password
  * ansible_ssh_private_key_file - Location of private key file
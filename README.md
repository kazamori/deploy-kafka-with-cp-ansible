# deploy-kafka-with-cp-ansible

Sample repository to deploy kafka with Confluent Platform

## Setup vagrant

Use [vagrant box](https://www.vagrantup.com/docs/boxes.html) to construct virtual environment.

In this case, select amazonlinux-2 as an example.

```bash
$ vagrant box add bento/amazonlinux-2  # only first time
```

Initialize virtualbox environment.

```bash
$ cp Vagrantfile into path/to/work/dir
$ cd path/to/work/dir
$ vagrant init bento/amazonlinux-2
```

Bootup guest OS and connect via ssh.

```bash
$ vagrant up
$ vagrant ssh
[vagrant@vagrant ~]$ uname -ar
Linux vagrant 4.14.154-128.181.amzn2.x86_64 #1 SMP Sat Nov 16 21:49:00 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

## Deploy with cp-ansible

### install ansible

```bash
$ pip install ansible
```

### set environment variable for vagrant

hosts.yml has some configuration for vagrant. it can be set via environment variables.

```bash
$ export VAGRANT_PORT=2222
$ export VAGRANT_PRIVATE_KEY="path/to/.vagrant/machines/default/virtualbox/private_key"
```

Confirm ansible can connect via ssh.

```bash
$ ansible -i hosts.yml all -m ping
```

Update DEFAULT_HASH_BEHAVIOUR.

```bash
$ export ANSIBLE_HASH_BEHAVIOUR="merge"
```

### deploy specified components

```bash
$ ansible-playbook -i hosts.yml cp-ansible/all.yml
```

### deploy specified components

```bash
$ ansible-playbook -i hosts.yml cp-ansible/all.yml --tags zookeeper,kafka_broker
```

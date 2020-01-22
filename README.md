# deploy-kafka-with-cp-ansible

Sample repository to deploy kafka with Confluent Platform

## Setup vagrant

write later

## Deploy with cp-ansible

```bash
$ pip install ansible
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

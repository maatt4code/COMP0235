# Week 4 - Mini Exercise

## Tasks
1. `variables.yaml` - so that everyone i on the same page and you don;t have to hardcode stuff
1. `requirements.yaml` - used for installing ansible modules
1. `inventory.yaml` - list oh nodes
```bash
# ALL - Install Modules - to skip first time known host fingerprint checks
ansible-playbook -i inventory.yaml --private-key=~/.ssh/lecturer_key 01_install_modules.yaml --ssh-common-args='-o StrictHostKeyChecking=no'

# Host - Create and Send Keys to Client and Cluster
ansible-playbook -i inventory.yaml --private-key=~/.ssh/lecturer_key 02_03_create_keys.yaml

# Client Format and Mount Storage

# Client - Start web Server
```
```bash
```

## Inventory
- `host`
  - This is where you set up your `client` (aka `master`) mahine from
  - Do the setup from here as your own laptop probably isn't Linux and therefore an be paiful
- [`client`](#client)
  - This is where you:
    - store data
    - control cluster nodes from
- [`cluster`](#cluster)
  - work hourse actually doing the monkey work

### <a name="client"></a> Client
This is the only machine with enough storage such that you can:
- format storage
- mount / point / link to the storage from your regular file system
- serve up data

So you probably want to:
1. set up webserver such that `cluster` nodes can get the data
1. xxx yyy zzz


### <a name="cluster"></a> Cluster Nodes
These
- are created by Lecturer for you
- have been configured to accept `leturer_key` for ssh
- have `ansible` already installed

## Security
### Security Group
None of these machines have security groups set up, so you can define whateer security group you like
### ssh
Options:
1. Have 1 set of keys for `client` <-> `cluster`
1. Have 2 set of keys:
    - 1 for `client` -> `cluster`; and
    - the other `client` <- `cluster`
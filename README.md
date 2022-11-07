# sui-node-automation
ansible configuration for [SUI Network](https://sui.io/)

## Documentation References

- [Sui fullnode documentation](https://docs.sui.io/devnet/build/fullnode)
- [Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html)

## Setting up control node

### Configure host

#### Install python
`curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`
`python3 get-pip.py --user`

#### Install ansible
`python3 -m pip install --user ansible`

#### Confirm installation
`source .profile`
`ansible --version`

### Set up SSH keys

Create key
` ssh-keygen -t ed25519 -C "youremail@gmail.com"`

Add the public key to the authorized_keys file
`echo "ssh-ed25519 <ed25519-PUBLIC-KEY youremail@gmail.com" >> $HOME/.ssh/authorized_keys`
```
eval `ssh-agent -s`
`ssh-add`
```

### Set up SUI playbook  

Clone this repo
`git clone https://github.com/0xzoz/sui-node-automation`

Edit inventory
`cd sui-ansible; cp inventory.yml.sample inventory.yml`

Add IP of target to `inventory.yml`

```
all:
  hosts: 
    sui_fullnode:
      ansible_host: <YOUR_TARGET_IP>
```

## Run Playbook
`cd sui-node-automation; ansible-playbook main.yml -i inventory.yml --e "target=sui_fullnode"`
## Licence


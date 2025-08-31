<<<<<<< HEAD
# ansible-linux-provisioning
Ansible playbook for provisioning Linux my "way"
=======
# Introduction
I've noticed that I tend to switch Linux distros or just reinstall the same one, so I made this script.

# Prerequisites
You need to have Ansible installed on the machine you're planning on running this script on, so you can just run this batch of commands to install it.
## Installing Ansible
### Option 1: If running Ubuntu
```sh
sudo apt update
sudo apt install -y ansible
ansible --version
```

### Option 2: Official Ansible PPA
```sh
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install -y ansible
ansible --version
```

## Configure the inventory
If you are running Ansible on the same machine, make sure your `inventory.ini` file looks like this:
```sh
[local_servers]
localhost ansible_connection=local
```
If not, you can use whatever `inventory.ini` or `inventory.yml` file configuration you want.

## Disable SSH host key checking
I know that from a security perspective, this isn't advisable, but since we are running it on our machines, I think it'll do fine.
### Through `ansible.cfg` file (permanent)
Edit the `ansible.cfg` file and change the `host_key_checking` setting to `false`:
```yml
[defaults]
host_key_checking = False
```
### Through `export` (temporary)
If you don't want this change in configuration to persist you can just disable it for this session by running this command in your terminal:
```sh
export ANSIBLE_HOST_KEY_CHECKING=False
```
## If you are not running this locally
You would need to copy your pub SSH key to the machine by running:
```sh
ssh-copy-id -i /path/to/your/pub_key username:ip-address
```
# Running the script
Since I'm still in the process of writing the script this part is subject to change. For now you can run this like:
```sh
ansible-playbook -i inventory.ini main-playbook.yml -u your-username
```
>>>>>>> initial-branch

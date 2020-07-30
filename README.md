# How to use Ansible and Github Action to Automate the Management of Docker Compose

## Description
This repo gives the ability to manage a remote server that runs a docker-compose file using Ansible and Github Action.

## Installation

### For Host Machine

#### Ansible 

For Mac OS, run the following command

```
brew install ansible
```
If you are using other OS, check out the official documentation [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

### For Remote Server

#### SSHPass

```
brew install https://raw.githubusercontent.com/kadwanev/bigboybrew/master/Library/Formula/sshpass.rb
```

Or you can install using the [source code](https://sourceforge.net/projects/sshpass/)

#### Python >=2.7
#### Pip
#### Docker SDK for Python

If you have python and pip installed. 
For python 2, simply run
```
pip install docker
```

For python 3
```
pip3 install docker
```
### PyYAML

python 2
```
pip install PyYAML
```
python 3
```
pip3 install PyYAML
```

### docker-compose
python 2
```
pip install docker-compose
```

python 3
```
pip3 install docker-compose
```

## Inventory

Create an inventory file and name it hosts.
```
your_host your_username your_password
```

You can encrypt your inventory file if you don't want to leak your confidential information

```
ansible-vault encrypt hosts
```
it will prompt to ask you password

to decrypt
```
ansible-vault decrypt hosts
```
## docker-compose.yml

The docker compose file that you will be using on the server

## Usage
Once you modified your docker-compose.yml on your local machine and you want to make it effective on the remote server, run
```
ansible-playbook -i path_to_inventory_file path_to_your_playbook --tags "scp, down, up"
```

If you made any change on this repo (e.g. edit Dockerfile), simply push the changes and Github Action will update the image and publish to your Docker Hub Registry.

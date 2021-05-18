# Orakuru Node Setup


## Installation

Playbook requires [ansible](https://www.ansible.com/) v2.9+ to run; and works only for Ubuntu:20.04

Install the dependencies and run the playbook.

Set the ENV Variables
```sh
export BSC_URL="https://bsc-dataseed.binance.org/" # replace with your url
export PRIVATE_KEY="key-here"
export ORAKURU_CORE_ADDRESS="core-address-here"
```
Now Install the lib dependencies
```sh
sudo apt update -y
sudo apt install ansible git -y
```

Run the playbook

```sh
git clone https://github.com/0x-cryptobuddha/orakuru-node-playbook.git
cd orakuru-node-playbook
ansible-playbook tasks/main.yml -vvv --extra-vars "node_name=your_node_name"
```

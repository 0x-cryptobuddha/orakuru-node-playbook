# Orakuru Node Setup


## Installation

Playbook requires [ansible](https://www.ansible.com/) v2.9+ to run; and works only for Ubuntu:20.04

Install the dependencies and run the playbook.

Set the ENV Variables
```sh
export BSC_URL="https://bsc-dataseed.binance.org/" # replace with your url
export PRIVATE_KEY="key-hereX"
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
ansible-playbook tasks/main.yml -vvv --extra-vars "node_name=your_node_name home_dir=ork_dir_location CB_CONFIG_DIR=config_dir"
```


Checking the status of node
```sh
supervisorctl status
```
Checking the logs

```sh
tail -f /var/log/orakuru-node.out.log

```

Upgrades
```sh
git clone https://github.com/0x-cryptobuddha/orakuru-node-playbook.git
cd orakuru-node-playbook
ansible-playbook tasks/build.yml -vvv --extra-vars "build_dir=/build git_tag=v0.2.3" -vvv
```
After this step do the following
```sh
sudo supervisorctl stop all
mv build_dir/bin/crystall_ball to data_dir
sudo supervisorctl start all
```


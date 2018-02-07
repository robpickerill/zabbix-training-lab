[![Build Status](https://travis-ci.org/robpickerill/zabbix-training-lab.svg?branch=master)](https://travis-ci.org/robpickerill/zabbix-training-lab)

# Zabbix Training Lab

Used to provision an ephemeral lab for Zabbix training on ec2 with amazon linux. This will build a number of single zabbix systems, with its own mysql backend. The following components will be installed on each ec2 instance:

- Zabbix web
- Zabbix server
- Zabbix agent
- Zabbix binaries:
  - zabbix_get
  - zabbix_sender
- Mariadb
- Httpd
- PHP
- Iptables

## Changing the number of instances

To change the number of instances required, either set the count variable in roles/deploy/defaults/main.yml, or pass in count=$requirednumber of instances via the command line:

ansible-playbook -i ec2.py site.yml -e count=15

## Pre-requisites

Ensure you have an aws access key and secret already configured on the shell environment variables, or with the relevant iam role for ec2 instance creation allocated to the instance from which ansible runs.

## Ansible Tags

The site.yml has two tags:

 - deploy, used to only deploy instances  
ansible-playbook -i ec2.py -t deploy site.yml

 - zabbix-server, used to only build zabbix-instances (please note you will need a static inventory for this, as the deploy role builds the dyanmic inventory)  
ansible-playbook -i hosts -t zabbix-server site.yml  

## Using this repository

To use this repository:

- Prepare  virtualenv:  
pip install virtualenv  
virtualenv --system-site-packages ansible  
source ansible/bin/activate  

- Install ansible in virtualenv:  
pip install ansible

- Clone the github repo:  
git clone https://github.com/robpickerill/zabbix-training-lab.git  
cd zabbix-training-lab

- Set variables and vault for ansible usage
export ANSIBLE_CONFIG=~/zabbix-training-lab/ansible.cfg  
echo 3vQuxIsH8YDAK/uhUpSWaAnpGKBqDlh8LEkAOlO/yj0= > ~/.vault

- Run ansible:
ansible-playbook -i ec2.py site.yml

# Zabbix Training Lab

Used to provision an ephemeral lab for Zabbix training on ec2 with amazon linux. This will build a number of single zabbix systems, with a mysql backend.

Ensure you have an aws access key and secret already configured on the shell environment variables, or with the relevant iam role for ec2 instance creation allocated to the instance from which ansible runs.

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

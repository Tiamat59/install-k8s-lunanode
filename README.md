# install-k8s-lunanode

This repository is here to set up a sandbox to train kubernetes students. Couple of  
scripts create the environment in Lunanode, a cloud service provider in Toronto, they have the lowest price.
for KVM virtual machines. Their service is awesome.   
  
see their website [here](https://www.lunanode.com/).

## First create all cluster VMs 
Get an API credentials from the lunanode website, see [here](https://dynamic.lunanode.com/panel/api)  
Save your API credentials in a file under your $HOME directory, change the line 7 in the file 
`create_vm_cluster.py` accordingly to your environment.   
This script is a quick and dirty experimental solution for 
setting up a cluster of 1 master and 2 nodes. It's linear so read it as it's be done and make some tests beforehand  
So I use to change it by naming each VM using a color reference, line 15 and test it in line 35  
(Note: I set a timer -line 25- for letting lunanode enough time for provisioning all public IP addresses for each VMs) 
 
## Inventory 
The create_vm_cluster script save all cluster ip addresse, password and user name in a file so you should change it 
accordingly to the following structure for your inventory file.   
```jsunicoderegexp
[node]
ip_address  ansible_ssh_user=ubuntu  ansible_ssh_pass=password ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
ip_address  ansible_ssh_user=ubuntu  ansible_ssh_pass=password ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
[master]
ip_address  ansible_ssh_user=ubuntu  ansible_ssh_pass=password ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
```
## And run the playbook !!!
Example:   
```ansible-playboox -i /home/hme/inventory-k8s-green playbook```
```ansible-playbook -i inventory --user romain --become --ask-become-pass playbook```

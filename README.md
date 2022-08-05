# CMAR 

configuration management using ansible-CMAR
we are going to install docker,jenkins,python using ansible roles
ansible-galaxy init CMAR 
tree . will give the tree structure created by ansible-galaxy

![image](https://user-images.githubusercontent.com/110584678/183070576-78ab5003-5141-4e82-a366-c49ee8afbf2d.png)
In this Task iam going to install Python,Ansible,Docker and Jenkins on  2 client Machines Whose ip’s are defined in tests/inventory
![image](https://user-images.githubusercontent.com/110584678/183070690-5b7e5a4e-945b-4984-8269-d1d7409e4b49.png)
ssh connection procedure is followed as 
--------------------------------------
in master
-----------
sudo su
wget https //dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
ls
-epel-release-latest-7.noarch.rpm
yum install epel-release-latest-7.noarch.rpm
yum install update -y
yum install git python python-level python-pip openssl ansible -y
vi /etc/ansible/hosts

give the host ips

vi /etc/ansible/ansible.cfg

uncomment inventory,sudo user

---->do these on all the master and nodes
adduser ansibul
passwd ansibul
exit 
from ansibul user
visudo
and add
ansibul ALL=(ALL) NOPASSWD: ALL

vi /etc/ssh/sshd_config

uncomment PermitRootLogin, PasswordAuthentication and comment another PasswordAuthentication

service sshd restart

in master
---------
 
ssh priv-ip-of node
in this mode we have to give the password
exit

ssh-keygen
enter enter enter

cd .ssh
ssh-copy-id username@priv-ip 

do this with all the nodes

cd ..
now 
ssh priv-ip-of node
now it will not ask any password

ansible all --list-hosts
----------------------------
check ssh connectivity
![image](https://user-images.githubusercontent.com/110584678/183071227-9cda8981-aaa4-4174-b4b9-fcb0b220537e.png)
run the playbook by using the command
ansible-playbook test.yml
u can check the node machines

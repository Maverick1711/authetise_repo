# USING ANSIBLE TO SPIN NGINX CONTAINER UP 
#### On your controller machine(e.g ubuntu OS ), install Ansible with the following commands.
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```
for other Operating systems visit Ansible official website, [click here](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)
####  Create a folder in your present working directory
```
$ mkdir Ansible

```
#### Copy the key generated while creating Ubuntu instance(Worker Node) into the Ansible Folder
```
$ cp ubuntu_key.pem ./Ansible

```
#### Change your directory into the Ansible Folder
```
$ cd Ansible

```
#### Inside the current directory git clone the files needed for the project and copy them into the Ansible folder from authetise_repo.
```
$ git clone https://github.com/Maverick1711/authetise_repo.git

```
#### copy them into the Ansible folder from authetise_repo.
```
$ cp authetise_repo/inventory authetise_repo/playbook.yaml .

```
#### Check the files you have in your present working directory
```
$ ls

```
#### You should get the following output
```
authetize_repo inventory playbook.yaml ubuntu_key.pem readme.me

```
#### Edit the inventory file with vim tool.( And it is also available in the Git Repository, kindly download it)
```
 vim inventory

```
#### Press key "I" to edit the inventory file. Change authetise(server name) could be replaced with any random name or URL to your server ansible_host= Private IP of the Ubuntu instance and user = Hostname of your instance and ansible_ssh_private_key_file=path_to_ubuntu-key.pem
```
Authetise ansible_host=172.31.17.252 ansible_user=ubuntu ansible_ssh_private_key_file=Ansible-controller-key.pem

```
#### Run the playbook with the following command.

```
ansible-playbook -i inventory playbook.yaml 
```

### NB - Security group of the controller node will be allowed to ssh into the worker node.
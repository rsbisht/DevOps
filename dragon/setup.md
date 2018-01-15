# How to setup the Environment

The following steps are involved in seting up the environment:

####   1. Install Oracle VirtualBox
####   2. Install Vagrant
####   3. Install Ansible

## Install VirtualBox

### 1). Download the VirtualBoxInstallation Kit

     # wget http://15.213.52.100:8080/repos/DevOps/VirtualBox/VirtualBox-5.1-5.1.26_117224_el7-1.x86_64.rpm

 ### 2). Install VirtualBox RPM

     #  yum localinstall VirtualBox-5.1-5.1.26_117224_el7-1.x86_64.rpm -y

###  3). Run VirtualBox Configuration

     # /sbin/vboxconfig

###  4). Validate the installation 

     # vboxmanage --version

###  5). Set the Path of Virtual Machines

     # mkdir -p /home/VirtualMachines

     # vboxmanage setproperty machinefolder /home/VirtualMachines


## Install Vagrant

### 1). Download the Vagrant Installation Kit

     # wget http://15.213.52.100:8080/repos/DevOps/Vagrant/vagrant_2.0.0_x86_64.rpm

###  2). Install Vagrant RPM

     #  yum localinstall vagrant_2.0.0_x86_64.rpm -y

###  3). Validate the installation

     # vagrant --version

###  5). Initialize Vagratnt environment

     # mkdir -p /home/projects/Vagrant/CentOS
     # cd /home/projects/Vagrant/CentOS
     # vagrant init centos/7


## Installing/Configuring Ansible

###  1). Create a Yum repo file (Ignore if alrady present)

     # wget http://15.213.52.100:8080/repos/DevOps/projects/dragon/playbooks/roles/common/files/RHEL_7.4.repo -P /etc/yum.repos.d

###  2). Install Ansible

     # yum install ansible -y

###  3). Create a Project directory (example)

    # mkdir -p /home/projects/dragon

###  4). Download the "dragon-playbooks.tar.gz"

     # wget http://15.213.52.100:8080/repos/DevOps/projects/dragon/dragon-playbooks.tar.gz -P /home/projects/dragon

###  5). Untar the "dragon-playbooks.tar.gz"

     # tar -xzvf dragon-playbooks.tar.gz -C /home/projects/dragon

###  6). Modify the "Vagrantfile" for No. of CPUs, Memory, Hostname, IP address etc.

###  7). Modify the "roles/<RoleName>/vars/main.yml" files for software location etc.

###  8). Update the "inventory/hosts" file (Example)

     # cat inventory/hosts

       [Dragon_Server_Hosts]
       192.168.2.20  ansible_ssh_user=root ansible_ssh_pass=vagrant

       [Dragon_Manager_Hosts]
       192.168.2.30  ansible_ssh_user=root ansible_ssh_pass=vagrant
_________________________________________________________________________________________________________________


### Start the VM


     # vagrant up --> (All)
     # vagrant up DRAGON_Server_01 -- (Selected VM)

### Check for running VMs

     # vagrant global-status
_________________________________________________________________________________________________________________


# Ansible
Create a ansible machine and control host machines 


To save the space in our system I am creating 3 hosts nodes(using centos 7) and 1 controler node(ubantu 20.) in virtual box.
using centos 7 


using ubantu
	sudo su -
	
	#install ansible
	sudo apt update
	sudo apt install software-properties-common
	sudo add-apt-repository --yes --update ppa:ansible/ansible
	sudo apt install ansible
	
	
	ip addr show
	
	#to make connection between controler machine and host machine 
	ssh-keygen
	ssh-copy-id root@192.168.1.10
	ansible -m ping 'test-servers'

using centos 7 

	#to install ansible
	sudo yum install epel-release
	sudo yum install ansible
	
	#to configure ip address
	cd /etc/sysconfig/network-scripts/
	cp ifcfg-enp0s3 ifcfg-enp0s8
	vi ifcfg-enp0s8
		#changes to make
		~comment out all ipv6 attributes and UUID
		BOOTPTOTO=none
		NAME=enp0s8
		DEVICE=enp0s8
		ONBOOT=no
		IPADDR=192.168.1.10
		PREFIX=24
	vi ifcfg-enp0s3
		#changes to make
		ONBOOT=yes
	ifup enp0s3
	ifup enp0s8
	cd
	ip addr show
	
	#to change the hostname
	vi /etc/hostname
	
	
	#to make connection between controler machine and host machine 
	ssh-keygen
	ssh-copy-id root@192.168.1.10
	ansible -m ping 'test-servers'
	
# to make ubantu available via ssh (remove error of connection refused on port 22)
sudo apt install openssh-server

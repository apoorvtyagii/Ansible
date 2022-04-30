# Ansible
Create a ansible machine and control host machines 



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

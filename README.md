# Vagrant-Python3
This repo is inteded as a base for building python3 projects. It comes as a Vagrant virtual machine running on top of VirtualBox with a shared folder shared between the two machines.

OS is Ubuntu 16.04
Ports opened for use:
	- guest: 80, host: 8080, host_ip: "127.0.0.1"
	- guest: 8000, host: 8000, host_ip: "127.0.0.1"

###Dependencies installed: 
	- VirtualEnv
	- Python3
	- Pip3

VirtualEnv file is created at root

###Usage
'''
# Ensure that you have vagrant box installed
vagrant box add V0rtex/xenial64

# Clone the repo
git clone

#startup vagrant machine and provision it
vagrant up

# Give guest additions to virtualbox
vagrant halt
vagrant plugin install vagrant-vbguest
vagrant reload

#ssh into the machine 
vagrant ssh

#turn off the machine
vagrant halt
'''


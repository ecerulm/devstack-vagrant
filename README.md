The `Vagrantfile` in this directory will



1. Download an ubuntu 13.10 base image
2. Startup a 2GB RAM virtual box with it
3. Provision that virtualbox 
	1. Install git
	- Install dos2unix
	- Clone devstack via git
	- copy local.conf from windows host to ubuntu /home/vagrant/devstack
- run the stack.sh

The `local.conf` provides setting for devstack like the passwords to use for each service. In this case all passwords are set to "secrete"
The Vagrant file in this directory will

Download an ubuntu 13.10 base image
Startup a 2GB RAM virtual box with it
Provision that virtualbox 
- Install git
- Install dos2unix
- Clone devstack via git
- copy local.conf from windows host to ubuntu /home/vagrant/devstack
- run the stack.sh

The local.conf provides setting for devstack like the passwords to use for each service. In this case all passwords are set to "secrete"
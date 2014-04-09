# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 
  config.vm.box = "chef/ubuntu-13.10-i386"

  config.vm.network "forwarded_port", guest: 80, host: 8081

  config.vm.provider "virtualbox" do |vb|
    # Don't boot with headless mode
    #vb.gui = true
  
    # Use VBoxManage to customize the VM. For example to change memory:
    #vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.memory = 2048
  end

$script=<<SCRIPT
sudo apt-get -y install git
sudo apt-get -y install dos2unix
SCRIPT
config.vm.provision "shell" do |s|
  s.inline = $script
  s.keep_color = true
end


$script=<<SCRIPT 
echo Run the stack.sh script
git clone https://github.com/openstack-dev/devstack.git
cp /vagrant/local.conf /home/vagrant/devstack/local.conf
dos2unix /home/vagrant/devstack/local.conf # make sure that is a unix file
cd /home/vagrant/devstack
./stack.sh
SCRIPT
config.vm.provision "shell" do |s|
  s.inline = $script
  s.keep_color = true
  s.privileged = false
end



end

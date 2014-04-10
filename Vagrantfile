# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 
  config.vm.box = 'hashicorp/precise64'
  #config.vm.box = 'preciseserver64'
  #config.vm.box_url =   'https://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box'


  config.vm.network "forwarded_port", guest: 80, host: 8081

  config.vm.provider "virtualbox" do |vb|
    # Don't boot with headless mode
    #vb.gui = true
  
    # Use VBoxManage to customize the VM. For example to change memory:
    #vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.memory = 4096
    vb.cpus = 2
  end

$script=<<SCRIPT
apt-get -y install git
apt-get -y install dos2unix
apt-get -y install vim
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
git checkout grizzly-eol
SCRIPT
config.vm.provision "shell" do |s|
  s.inline = $script
  s.keep_color = true
  s.privileged = false
end



end

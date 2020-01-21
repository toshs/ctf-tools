# -*- mode: ruby -*-
# vi: set ft=ruby :

$bootstrap = <<SCRIPT
sudo apt-get update
sudo apt-get -fuy -o Dpkg::Options::='--force-confold' install git

git clone https://github.com/toshs/ctf-tools.git /home/vagrant/ctf-tools/
/home/vagrant/ctf-tools/bin/manage-tools -s setup

git clone https://github.com/toshs/dotfiles.git /home/vagrant/dotfiles/
cd /home/vagrant/dotfiles/
./install.sh
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "ctf-tools"
  config.vm.provision "shell", privileged: false, inline: $bootstrap
  config.vbguest.installer_arguments = []
end

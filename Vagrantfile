# -*- mode: ruby -*-
# vi: set ft=ruby :

$bootstrap = <<SCRIPT
sudo perl -p -i.bak -e 's%https?://(?!security)[^ \t]+%http://jp.archive.ubuntu.com/ubuntu/%g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get -fuy -o Dpkg::Options::='--force-confold' install git
sudo apt-get -y install zsh
sudo chsh vagrant -s `which zsh` 

git clone https://github.com/toshs/ctf-tools.git /home/vagrant/ctf-tools/
/home/vagrant/ctf-tools/bin/manage-tools -s setup

git clone https://github.com/toshs/dotfiles.git /home/vagrant/dotfiles/ --recursive
cd /home/vagrant/dotfiles/
./install.sh
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "security-tools"
  config.vm.provision "shell", privileged: false, inline: $bootstrap
  config.vm.synced_folder "~/CTF", "/CTF"
  config.ssh.forward_x11 = true
  config.vbguest.installer_arguments = []
end

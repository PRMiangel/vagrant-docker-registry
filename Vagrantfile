# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
   config.vm.box_check_update = false
   config.vm.network "public_network"
   config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = "1024"     
   end
   config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     curl -fsSL get.docker.com -o get-docker.sh
     sh get-docker.sh
     sudo usermod -aG docker vagrant
     sudo docker pull registry
     sudo docker run -d -p 5000:5000 --restart=always --name registry registry
   SHELL
end

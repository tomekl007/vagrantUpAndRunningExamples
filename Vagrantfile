# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"
  #config.vm.provision "docker" do |d|
  #    end

    config.vm.define "db" do |db|
      db.vm.provision "shell", path: "db_provision.sh"
      db.vm.network :private_network, ip: "192.168.33.11"
      # We'll fill this in soon.
    end

    #config.ssh.forward_agent = true

    config.vm.define "web" do |web|
    #  web.vm.provision "docker" do |d|
    #  end
      web.vm.network "forwarded_port", guest: 80, host: 8092
      web.vm.provision "shell", path: "provision.sh"
      web.vm.provision :shell, inline: "apt-get install -y mysql-client"
      web.vm.provision :shell, inline: "curl -sSL https://get.docker.io/ubuntu/ | sudo sh"
      web.vm.network :private_network, ip: "192.168.33.10" # default subnet mask is 255.255.255.0
    end
end

#Vagrant.configure("2") do |config|
#  config.vm.box = "hashicorp/precise32"
#  config.vm.network "forwarded_port", guest: 80, host: 8090
#end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
    config.vm.boot_timeout = 600
    config.vm.box = "ubuntu/bionic64"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
   end

    config.vm.box_download_insecure=true
    config.vm.provision :docker
    #config.vm.provision :docker_compose

  #VM ci-server
    config.vm.define "server-1" do |ci|
      ci.vm.network "private_network", ip: '192.168.56.15'
      ci.vm.hostname = "ciserver"
      ci.vm.provision :file, source:"../docker/docker-compose.ci.yml", destination:"docker-compose.yml"
      ci.vm.provision :docker_compose, yml:"/home/vagrant/docker-compose.yml", run: "always"
    end
  #VM server-2
    #config.vm.define "server-2" do |server_2|
      #server_2.vm.network "private_network", ip: '192.168.56.16'
      #server_2.vm.hostname = "server-2"
      #server_2.vm.provision :file, source: "converter_service", destination: "converterService"
    #end  
end

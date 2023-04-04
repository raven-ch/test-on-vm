# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
   config.vm.box = "bento/ubuntu-22.04"
   config.vm.box_url = "file:/home/artemiy/vagrant/images/e802b53a-d080-4a9e-a24c-9d3ba7c1fc8f"
   config.vm.box_check_update = false
  
   config.vm.define "consul" do |consul|
      consul.vm.network "private_network", ip: "10.10.0.2"
      consul.vm.hostname = "consul"  
      consul.vm.provider "virtualbox" do |vb|
          vb.memory = "1024"
          vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
          vb.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
       end
   end
 
   
  config.vm.define "redis-master" do |master|
      master.vm.network "private_network", ip: "10.10.0.10"
      master.vm.hostname = "redis-master"  
      master.vm.provider "virtualbox" do |vb|
          vb.memory = "1024"
          vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
          vb.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
      end
  end
 
 
  config.vm.define "redis-slave1" do |slave1|
      slave1.vm.network "private_network", ip: "10.10.0.11"
      slave1.vm.hostname = "redis-slave1"  
      slave1.vm.provider "virtualbox" do |vb|
          vb.memory = "1024"
          vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
          vb.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
      end
  end
 
  config.vm.define "redis-slave2" do |slave2|
      slave2.vm.network "private_network", ip: "10.10.0.12"
      slave2.vm.hostname = "redis-slave2"  
      slave2.vm.provider "virtualbox" do |vb|
          vb.memory = "1024"
          vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
          vb.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
      end
  end
 
end

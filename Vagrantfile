# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
config.vagrant.plugins = "vagrant-vbguest"
ENV['VAGRANT_NO_PARALLEL'] = 'yes'
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.define "db" do |db|
     db.vbguest.auto_update = false  
     db.vm.box = "centos/7"
     db.vm.hostname = "db"
     db.vm.network "private_network", :ip => '192.168.0.10'
     config.vm.provider "virtualbox" do |vb_db|
      vb_db.gui = false
      vb_db.memory = "2048"
     end
     config.vm.provision "ansible" do |ansible_db|
         ansible_db.playbook = "pgsql.yaml"
      ansible_db.compatibility_mode = "2.0"
     end
  end

  config.vm.define "db1" do |db1|
     db1.vbguest.auto_update = false  
     db1.vm.box = "centos/7"
     db1.vm.hostname = "db1"
     db1.vm.network "private_network", :ip => '192.168.0.11'
     config.vm.provider "virtualbox" do |vb_db1|
      vb_db1.gui = false
      vb_db1.memory = "2048"
     end
     config.vm.provision "ansible" do |ansible_db1|
         ansible_db1.playbook = "pgsql1.yaml"
      ansible_db1.compatibility_mode = "2.0"
     end
  end

 config.vm.define "bal" do |bal|
     bal.vm.synced_folder ".", "/vagrant"
     bal.vbguest.auto_update = false
     bal.vm.box = "centos/7"
     bal.vm.hostname = "bal1"
     bal.vm.network "private_network", :ip => '192.168.0.100'
     bal.vm.network "forwarded_port", guest: 80, host: 8080
     config.vm.provider "virtualbox" do |vb_app|
      vb_app.gui = false
      vb_app.memory = "512"
     end
     config.vm.provision "ansible" do |ansible_app|
         ansible_app.playbook = "bal.yaml"
      ansible_app.compatibility_mode = "2.0"
     end
  end

  
  config.vm.define "app" do |app|
     app.vm.synced_folder ".", "/vagrant"
     app.vbguest.auto_update = false
     app.vm.box = "centos/7"
     app.vm.hostname = "app"
     app.vm.network "private_network", :ip => '192.168.0.20'
#     app.vm.network "forwarded_port", guest: 80, host: 8080
     config.vm.provider "virtualbox" do |vb_app|
      vb_app.gui = false
      vb_app.memory = "1024"
     end
     config.vm.provision "ansible" do |ansible_app|
         ansible_app.playbook = "app.yaml"
      ansible_app.compatibility_mode = "2.0"
     end
  end

 config.vm.define "app1" do |app1|
     app1.vm.synced_folder ".", "/vagrant"
     app1.vbguest.auto_update = false
     app1.vm.box = "centos/7"
     app1.vm.hostname = "app"
     app1.vm.network "private_network", :ip => '192.168.0.21'
     config.vm.provider "virtualbox" do |vb_app1|
      vb_app1.gui = false
      vb_app1.memory = "1024"
     end
     config.vm.provision "ansible" do |ansible_app1|
         ansible_app1.playbook = "app1.yaml"
      ansible_app1.compatibility_mode = "2.0"
     end
  end

end

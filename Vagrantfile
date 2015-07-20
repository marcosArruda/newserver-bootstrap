# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure(2) do |config|
  config.vm.box = "marruda/trusty64-java-all"
  config.vm.provider "virtualbox" do |allvm|
    allvm.gui = false
    allvm.memory = "512"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "create-users.yml"
    ansible.verbose = "vv"
  end
  config.vm.define "tomcat1" do |tomcat1|
    tomcat1.vm.hostname = "tomcat1"
    #tomcat1.vm.network "forwarded_port", guest: 80, host: 8080
    tomcat1.vm.network "private_network", ip: "192.168.56.101"

  end

  config.vm.define "tomcat2" do |tomcat2|
    tomcat2.vm.hostname = "tomcat2"
    #tomcat2.vm.network "forwarded_port", guest: 80, host: 8080
    tomcat2.vm.network "private_network", ip: "192.168.56.102"
  end

  #tomcat2.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "bootstrap.yml"
  #  ansible.verbose = "vv"
    # ansible.verbose = "vvvv"
  #end
end

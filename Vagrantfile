# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "marruda/trusty64-java-all"

  config.vm.provider "virtualbox" do |allvm|
    allvm.gui = false
    allvm.memory = "512"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "basic-configuration.yml"
    #ansible.verbose = "vv"
  end

  config.vm.define "tomcat1" do |tomcat1|
    tomcat1.vm.hostname = "tomcat1"
    tomcat1.vm.network "private_network", ip: "192.168.56.101"
    tomcat1.vm.provision "ansible" do |tomcat1_ansible|
      tomcat1_ansible.playbook = "install-tomcat7.yml"
      tomcat1_ansible.inventory_path = "hosts"
    end
    #tomcat1.vm.network "forwarded_port", guest: 80, host: 8080
  end

  config.vm.define "tomcat2" do |tomcat2|
    tomcat2.vm.hostname = "tomcat2"
    tomcat2.vm.network "private_network", ip: "192.168.56.102"
    tomcat2.vm.provision "ansible" do |tomcat2_ansible|
      tomcat2_ansible.playbook = "install-tomcat7.yml"
      tomcat2_ansible.inventory_path = "hosts"
    end
    #tomcat2.vm.network "forwarded_port", guest: 80, host: 8080
  end

  config.vm.define "db1" do |db1|
    db1.vm.hostname = "db1"
    db1.vm.network "private_network", ip: "192.168.56.103"
    db1.vm.provision "ansible" do |db1_ansible|
      db1_ansible.playbook = "install-postgres9.4.yml"
      db1_ansible.inventory_path = "hosts"
    end
  end

  config.vm.define "loadbalancer1" do |loadbalancer1|
    loadbalancer1.vm.hostname = "loadbalancer1"
    loadbalancer1.vm.network "private_network", ip: "192.168.56.104"
    #sudo add-apt-repository -y ppa:vbernat/haproxy-1.5
    #sudo apt-get update
    #sudo apt-get install -y haproxy

    #https://serversforhackers.com/load-balancing-with-haproxy
  end

  config.vm.define "monitoring1" do |monitoring1|
    monitoring1.vm.hostname = "monitoring1"
    monitoring1.vm.network "private_network", ip: "192.168.56.105"
  end
end

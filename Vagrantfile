# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure(2) do |config|
  config.vm.box = "marruda/trusty64-java-all"

  # Disable automatic box update checking.
  # config.vm.box_check_update = false

  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM.
  # config.vm.synced_folder "../host_path", "/guest_path"



   config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.network "forwarded_port", guest: 80, host: 8080
    node1.vm.network "private_network", ip: "192.168.56.101"
    node1.vm.provider "virtualbox" do |vbnode1|
      vbnode1.gui = false
      vbnode1.memory = "1024"
    end

    node1.vm.provision "ansible" do |ansible|
      ansible.playbook = "bootstrap.yml"
      ansible.verbose = "vvvv"
      # ansible.verbose = "vvvv"
    end
  end

  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
end

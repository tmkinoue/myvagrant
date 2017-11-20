# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.define "ubuntu1604" do |node|
    node.vm.box = "ubuntu/xenial64"
    node.vm.hostname = "ubuntu1604"
    node.vm.network :private_network, ip: "192.168.33.10"
    node.vm.provider :virtualbox do |vb|
      vb.name = "ubuntu1604"
    end
    node.vm.provision "shell",  inline: <<-SHELL
      apt-get update
      apt-get install -y whois python-setuptools
      useradd -p `echo vagrant | mkpasswd -s -m sha-512` -m -s '/bin/bash' vagrant
      gpasswd -a vagrant sudo
      apt-get install -y python-setuptools build-essential libssl-dev libffi-dev python-dev sshpass
      easy_install pip
      pip install ansible
      echo 'vagrant ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/vagrant
    SHELL
  end
  # config.vm.define "deploy" do |node|
  #   node.vm.box = "ubuntu/xenial64"
  #   node.vm.hostname = "deploy"
  #   node.vm.network :private_network, ip: "192.168.33.11"
  #   node.vm.provider :virtualbox do |vb|
  #     vb.name = "deploy"
  #   end
  #   node.vm.provision "shell",  inline: <<-SHELL
  #     apt-get update
  #     apt-get install -y whois python-setuptools
  #     useradd -p `echo vagrant | mkpasswd -s -m sha-512` -m -s '/bin/bash' vagrant
  #     gpasswd -a vagrant sudo
  #     apt-get install -y python-setuptools build-essential libssl-dev libffi-dev python-dev sshpass
  #     easy_install pip
  #     pip install ansible
  #     echo 'vagrant ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/vagrant
  #   SHELL
  # end
  # config.vm.define "web" do |node|
  #   node.vm.box = "ubuntu/xenial64"
  #   node.vm.hostname = "web01"
  #   node.vm.network :private_network, ip: "192.168.33.21"
  #   node.vm.provider :virtualbox do |vb|
  #     vb.name = "web01"
  #   end
  #   node.vm.provision "shell",  inline: <<-SHELL
  #     apt-get update
  #     apt-get install -y whois python-setuptools
  #     useradd -p `echo vagrant | mkpasswd -s -m sha-512` -m -s '/bin/bash' vagrant
  #     gpasswd -a vagrant sudo
  #     echo 'vagrant ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/vagrant
  #   SHELL
  # end
  # config.vm.define "dbmaster" do |node|
  #   node.vm.box = "ubuntu/xenial64"
  #   node.vm.hostname = "db01"
  #   node.vm.network :private_network, ip: "192.168.33.31"
  #   node.vm.provider :virtualbox do |vb|
  #     vb.name = "dbmaster"
  #   end
  #   node.vm.provision "shell",  inline: <<-SHELL
  #     apt-get update
  #     apt-get install -y whois python-setuptools
  #     useradd -p `echo vagrant | mkpasswd -s -m sha-512` -m -s '/bin/bash' vagrant
  #     gpasswd -a vagrant sudo
  #     echo 'vagrant ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/vagrant
  #   SHELL
  # end
  # config.vm.define "dbslave" do |node|
  #   node.vm.box = "ubuntu/xenial64"
  #   node.vm.hostname = "db02"
  #   node.vm.network :private_network, ip: "192.168.33.32"
  #   node.vm.provider :virtualbox do |vb|
  #     vb.name = "dbslave"
  #   end
  #   node.vm.provision "shell",  inline: <<-SHELL
  #     apt-get update
  #     apt-get install -y whois python-setuptools
  #     useradd -p `echo vagrant | mkpasswd -s -m sha-512` -m -s '/bin/bash' vagrant
  #     gpasswd -a vagrant sudo
  #     echo 'vagrant ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/vagrant
  #   SHELL
  # end
 
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
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

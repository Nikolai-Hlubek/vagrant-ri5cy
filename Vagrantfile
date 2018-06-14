# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "bento/ubuntu-18.04"
  
  config.vm.boot_timeout = 600

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 8888 on the guest machine.
  #config.vm.network "forwarded_port", guest: 8888, host: 8088

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"

  end

  # Enable provisioning with a shell script.
  # Install prerequisits for building gcc toolchain
  config.vm.provision "shell", inline: <<-SHELL

    apt-get update
    apt-get install -y virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11

    apt-get install -y texinfo
    apt-get install -y libmpc-dev
    apt-get install -y g++

    apt-get install -y lubuntu-desktop
    apt-get install -y scite

  SHELL

  # Provision as user vagrant
  # Download makefile for gcc toolchain from github
  # build the gcc toolchain for ri5cy
  # the build requires unrestriced internet access because it pulls in other git archives and uses ftp
  # the build will take around 1h
   
  $script = <<-SHELL

    git clone https://github.com/TobiasKaiser/ri5cy_gnu_toolchain.git ri5cy
    cd ri5cy
    make

  SHELL

  config.vm.provision "shell", privileged: false, inline: $script

end

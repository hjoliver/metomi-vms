# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "metomi-vm-ubuntu-1404-lisbon"
  config.vm.box = "ubuntu/trusty64"
  # Remove "desktop" from the args below if only accessing via SSH
  # Remove "mosrs" from the args below if not accessing the Met Office Science Repository Service
  config.vm.provision :shell, path: "install.sh", args: "ubuntu 1404 desktop mosrs"
  config.ssh.forward_x11 = true

  config.vm.provider "virtualbox" do |v|
    v.name = "metomi-vm-ubuntu-1404-lisbon"
    # Comment out the line below if only accessing via SSH
    v.gui = true
    # Modify the line below if you need more than 1GB RAM
    v.memory = 1024
    v.cpus = 2
  end

end

# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.forward_agent = false

  config.vm.box = "../package.box"
  #config.vm.network "private_network", ip: "192.168.43.40"
  config.vm.network "public_network", ip: "192.168.99.50"
  config.vm.synced_folder ".", "/var/www/html"

  config.vm.provider "virtualbox" do |v, override|
    v.customize ["modifyvm", :id, "--rtcuseutc", "on"]
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "90"]
    v.customize ["modifyvm", :id, "--memory", "1024"]
    v.customize ["modifyvm", :id, "--cpus", "1"]
  end

  config.vm.provider :vmware_fusion do |v, override|
    v.vmx["memsize"] = "1024"
    v.vmx["numvcpus"] = "1"
  end

  config.vm.provider :parallels do |v, override|
    v.memory = 1024
    v.cpus = 1
  end
end
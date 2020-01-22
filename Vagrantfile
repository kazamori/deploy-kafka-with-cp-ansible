# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/amazonlinux-2"

  # http
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # kafka
  [9091, 9092, 9021, 8083, 8088, 8082, 8081, 2181, 2888, 3888].each do |port|
    config.vm.network "forwarded_port", guest: port, host: port
  end

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = 2048
  end
end

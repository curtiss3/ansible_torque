# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "master" do |master|

    master.vm.provider 'virtualbox' do |vb|
      vb.cpus = 2
      vb.memory = 4096
    end
    master.vm.network "private_network", ip: "192.168.50.4"
    master.vm.hostname = "master"

    master.vm.box = "bento/centos-7.3"

    master.vm.provision "shell", inline: <<-SHELL
      yum install -y epel-release
      yum install -y python-pip
      yum install -y python-devel
      yum group install -y "Development Tools"
      yum install -y openssl-devel
      pip install --upgrade pip
      pip install virtualenv
      pip install ansible
    SHELL
  end

  config.vm.define "client1" do |box|

    box.vm.provider 'virtualbox' do |vb|
      vb.cpus = 1
      vb.memory = 2048
    end
    box.vm.network "private_network", ip: "192.168.50.5"
    box.vm.hostname = "client1"

    box.vm.box = "bento/centos-7.3"
  end
end

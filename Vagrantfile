# -*- mode: ruby -*-
# vi: set ft=ruby :

# This Vagrantfile configuration emulates the AWS OpsWorks example project found
# in their "Getting Started" guide:
# http://docs.aws.amazon.com/opsworks/latest/userguide/gettingstarted-db.html

Vagrant.configure("2") do |config|

  config.vm.box = "centos7mini-opsworks"
  # config.vm.box_url = "http://sartre.ugent.be/bt/vagrant/boekentoren.box"

  # Create the php-app layer
  config.vm.define "app" do |layer|

    layer.vm.provision "opsworks", type:"shell", args:[
      'ops/dna/stack.json',
      'ops/dna/php-app.json'
    ]

    # Forward port 80 so we can see our work
    layer.vm.network "forwarded_port", guest: 80, host: 8080
    layer.vm.network "private_network", ip: "192.168.56.11"

    layer.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "768"]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
  end

  # Create the db-master layer
  config.vm.define "db" do |layer|

    layer.vm.provision "opsworks", type:"shell", args:[
      'ops/dna/stack.json',
      'ops/dna/db-master.json'
    ]

    layer.vm.network "private_network", ip: "192.168.56.21"

	layer.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
  end
end
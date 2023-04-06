# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"
     
    config.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 1
    end
  
    boxes = [
      { :name => "ipa.otus.lan", :ip => "192.168.56.10" },
      { :name => "client1.otus.lan", :ip => "192.168.56.11" },
      { :name => "client2.otus.lan", :ip => "192.168.56.12" }
    ]

    boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.network "private_network", ip: opts[:ip]
        
        if opts[:name] == "client2.otus.lan"
          config.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/provision.yml"
            ansible.inventory_path = "ansible/hosts"
            ansible.host_key_checking = "false"
            ansible.limit = "all"
          end
        end
      end
    end
  end

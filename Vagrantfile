# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.ssh.insert_key = false
  config.vm.box = 'centos/7'

  servers = {
    "smtprelay1": "10.0.0.10",
  }

  groups = {
    "alfresco": ['smtprelay']
  }
  
  servers.each do |server, ip|
    config.vm.define "#{server}" do |node|
      node.vm.hostname = "#{server}"
      node.vm.network 'private_network', ip: "#{ip}"
      node.vm.network "forwarded_port", guest: 8025, host: 25
    end
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'test.yml'
    ansible.groups = groups
  end

end

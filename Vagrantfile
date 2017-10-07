# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.network 'private_network', ip: '192.168.100.100' 
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '2048'
    vb.cpus = '1'
    vb.name = 'ubuntu'
  end
  
  # @todo Get guest vm ip and set host file for ansible and windows
  # @todo Configuration in json file and supports multiple playbooks
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end

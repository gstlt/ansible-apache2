# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|

  # Ensure we use our vagrant private key
  #config.ssh.username = 'vagrant'
  #config.ssh.password = 'vagrant'
  config.ssh.insert_key = false
  config.ssh.private_key_path = '~/.vagrant.d/insecure_private_key'

  config.vm.define 'vagrant-test' do |machine|
    #machine.vm.box = "ubuntu/xenial64"
    machine.vm.box = "ubuntu/wily64"
    #machine.vm.box = "ubuntu/trusty64"
    #machine.vm.box = "debian/wheezy64"
    #machine.vm.box = "chef/centos-7.1"

    machine.vm.network :private_network, ip: '192.168.88.22'
    machine.vm.hostname = 'vagrant-test.local'
    machine.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'tests/playbook.yaml'
      ansible.inventory_path = 'vagrant-inventory'
      ansible.limit = "all"
      ansible.host_key_checking = false
    end

  end

end

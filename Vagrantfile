# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = '2'
Vagrant.require_version '>= 1.5.0'
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = 'local-dev'
  config.omnibus.chef_version = 'latest'
  config.vm.box = 'ubuntu/trusty64'
  config.vm.network :private_network, type: 'dhcp'
    config.vm.network "private_network", ip: "192.168.50.20"
  config.vm.synced_folder "./data", "/data"
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = [:host, "cookbooks"]
    chef.provisioning_path = "/vagrant-chef"
    chef.json = {
    }
    chef.run_list = [
      'recipe[crockpot::default]'
    ]
  end
end
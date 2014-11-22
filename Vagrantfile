# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network :private_network, ip: "192.168.27.100"
  # config.vm.network :public_network
  
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider :virtualbox do |vb|
    # Don't boot with headless mode
    # vb.gui = true

    # Use VBoxManage to customize the VM. For example to change memory:
    vb.memory = 4096
    vb.cpus = 2
  end

  # View the documentation for the provider you're using for more
  # information on available options.
  config.vm.provision :ansible do |ansible|
    ansible.limit = "all"
    ansible.sudo = true
    ansible.sudo_user = "root"
    ansible.playbook = "devstack/devstack.yml"
    ansible.inventory_path = "devstack/hosts"
    ansible.verbose = true
  end
end

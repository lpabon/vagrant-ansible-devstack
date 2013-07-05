# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "hackerbox_precise64"
  # config.vm.box_url = "https://www.dropbox.com/s/uzuc3h5p7tysin2/hackerbox_precise64.box"

  config.vm.network :private_network, ip: "192.168.27.100"
  # config.vm.network :public_network
  
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider :virtualbox do |vb|
    # Don't boot with headless mode
    # vb.gui = true

    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  # View the documentation for the provider you're using for more
  # information on available options.
  config.vm.provision :ansible do |ansible|
    ansible.subo = true
    ansible.sudo_user = "root"
    ansible.playbook = "devstack/devstack.yml"
    ansible.inventory_file = "devstack/hosts"
    ansible.verbose = true
  end
end
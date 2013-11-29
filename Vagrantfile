# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = 'ringtail64-rvm'
  config.vm.box_url ="https://dl.dropboxusercontent.com/u/6154794/Vagrant/ringtail64-rvm.box"
  config.vm.network :private_network, ip: "192.168.33.10"
  config.ssh.forward_agent = true
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  config.vm.synced_folder "~/src", "/vagrant", id: "vagrant-root"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
    chef.add_recipe "recipe[apt]"
    chef.add_recipe "recipe[build-essential]"
    chef.add_recipe "recipe[nodejs]"
    chef.add_recipe "recipe[npm]"
    chef.add_recipe "recipe[git]"
    chef.add_recipe "recipe[tree]"
    chef.add_recipe "recipe[js]"
  end
end

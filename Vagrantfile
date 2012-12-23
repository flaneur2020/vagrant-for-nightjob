# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "ubuntu-precise-64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "chef/cookbooks"
    chef.add_recipe %w{build-essential python ruby apt vim zsh }


    chef.json = {
      :rvm => {
        :user => 'vagrant',
        :default_ruby => '1.9.3',
        :rubies => ['1.9.3']
      }
    }
  end
end

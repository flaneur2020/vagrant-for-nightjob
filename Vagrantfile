# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "ubuntu-precise-64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.host_name = 'nightjob'
  config.vm.customize [
    'modifyvm', :id,
    '--name', 'Nightjob',
    '--memory', '512',
  ]

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    %w{ 
      rvm::system rvm::vagrant 
      python build-essential 
      vim git tmux ack zsh
    }.each do |recipe|
      chef.add_recipe recipe
    end

    chef.json = {
      :rvm => {
        :user => 'vagrant',
        :default_ruby => '1.9.3',
        :rubies => ['1.9.3'],
        :global_gems => [
          { :name => 'rake' },
          { :name => 'bundler' }
        ]
      }
    }
  end
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "Debian7"
  config.vm.box_url = "https://opscode-vm-bento.s3.amazonaws.com/vagrant/opscode_debian-7.1.0_provisionerless.box"
  config.vm.network :private_network, ip: "192.168.33.10"

  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.berkshelf.enabled = true
  config.omnibus.chef_version = :latest

  config.vm.provision :chef_solo do |chef|
    chef.run_list = [
      "mysql::client",
      "mysql::server",
      "hello"
    ]

    chef.json = {
      mysql: {
        server_root_password: "iloverandompasswordsbutthiswilldo",
        server_repl_password: "iloverandompasswordsbutthiswilldo",
        server_debian_password: "iloverandompasswordsbutthiswilldo",
        bind_address: "127.0.0.1"
      }
    }
  end

end

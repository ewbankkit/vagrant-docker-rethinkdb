# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false

  # vagrant plugin install vagrant-proxyconf
  if Vagrant.has_plugin?("vagrant-proxyconf")
    if ENV["http_proxy"]
      config.proxy.http = ENV["http_proxy"]
    else
      config.proxy.http = false
    end
    if ENV["https_proxy"]
      config.proxy.https = ENV["https_proxy"]
    else
      config.proxy.https = false
    end
    if ENV["no_proxy"]
      config.proxy.no_proxy = ENV["no_proxy"]
    else
      config.proxy.no_proxy = false
    end
  end

  config.vm.define "rethinkdb-in-a-box" do |e|
    # Download from Atlas.
    # Ubuntu 14.04 LTS 64-bit server with Puppet.
    e.vm.box = "puppetlabs/ubuntu-14.04-64-puppet"
    e.vm.box_version = "1.0.1"

    e.vm.hostname = "rethinkdb-in-a-box"

    # RethinkDB:
    e.vm.network :forwarded_port, guest: 8080, host: 8080

    e.vm.provider "virtualbox" do |vb|
      vb.name = "rethinkdb-in-a-box"
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    e.vm.provision "shell" do |shell|
      shell.path = "scripts/startup.sh"
    end

    e.vm.provision :puppet do |puppet|
      puppet.manifests_path = "puppet/manifests"
      puppet.manifest_file  = "init.pp"
    end
  end
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

ENV['VAGRANT_DEFAULT_PROVIDER'] ||= 'docker'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.username = "root"
  config.ssh.private_key_path = "./host/phusion.key"

  config.vm.define "felix" do |felix|
    # php.vm.network "private_network", ip: "192.168.33.11"

    felix.vm.provider "docker" do |docker|
      docker.vagrant_vagrantfile = "./host/Vagrantfile"
      docker.build_dir = './felix'

      docker.name = 'felix'

      # Because Vagrant goofs up the ip address thing
      # docker.ports << '192.168.33.10:80:80'
      docker.create_args = [ '-p', '192.168.33.10:80:80' ]
    end
  end

  config.vm.define "oscar" do |oscar|
    # testy.vm.network "private_network", ip: "192.168.33.12"

    oscar.vm.provider "docker" do |docker|
      docker.vagrant_vagrantfile = "./host/Vagrantfile"
      docker.build_dir = './oscar'

      docker.name = "oscar"

      # Because Vagrant goofs up the ip address thing
      # docker.ports << '192.168.33.11:80:80'
      docker.create_args = [ '-p', '192.168.33.11:80:80' ]
    end
  end

  # config.ssh.pty = true
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

Vagrant.configure("2") do |config|

  # config.vm.provision "shell", inline: <<-SHELL
  # echo "========SUCCESS========"
  # SHELL

  config.vm.define "windows10" do |config|
  # config.vm.define "windows10", autostart: false do |config|
  config.vm.box              = "windows10"

  config.vm.box_check_update = false
    config.vm.provider :libvirt do |v|
      v.qemu_use_session = false
      v.cpus             = 2
      v.memory           = 4086
    end
  end

end
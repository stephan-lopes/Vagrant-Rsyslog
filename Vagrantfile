# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.hostname = "rsyslog.local"

  config.vm.box_check_update = true

  config.vm.provider "virtualbox" do |vb|
    vb.name   = "rsyslog"
    vb.memory = "512"
    vb.cpus   = "1"
    vb.gui    = false
  end

  config.vm.provision "shell", inline: <<-SHELL
    yum update -y
    yum install epel-release -y
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook          = "ansible/playbook.yml"
    ansible.galaxy_role_file  = "ansible/requirements.yml"
  end
end

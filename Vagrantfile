# -*- mode: ruby -*-
# vi: set ft=ruby :

#######################################
## this is a minimalist vagrant file ##
#######################################
#
Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"
  #################################################################################################
  #  this stuff is a red herring, but you'll see it everywhere online to try to get ssh working  ##
  #################################################################################################
  # config.ssh.insert_key = false
  # config.ssh.forward_agent = true
  # config.ssh.username = "vagrant"
  # config.ssh.password = "vagrant"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  ###########################################################################
  # this is the magic that gets ssh working.  Normal ssh, not vagrant ssh  ##
  ###########################################################################
  config.vm.provision "shell", inline: <<-SHELL
     sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
     systemctl restart sshd.service
  SHELL
end

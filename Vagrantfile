# -*- mode: ruby -*-
# vi: set ft=ruby :

$script_to_install_ansible = <<SCRIPT
echo Installing Ansible...

# Configure EPEL repository - Ansible is part of Extra Packages for Enterprise Linux (EPEL)
rpm -iUvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm

# Update our packages
yum -y update

# Install ansible
yum -y install ansible
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"

  config.vm.provision "shell", privileged: true,
    inline: $script_to_install_ansible
end
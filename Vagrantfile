# -*- mode: ruby -*-
# vi: set ft=ruby :

# Fill out these!
# Or, even better, define them in your environment
ENV['http_proxy'] =
ENV['https_proxy'] = "#{ENV['http_proxy']}"

required_plugins = %w(vagrant-proxyconf)

plugins_to_install = required_plugins.select { |plugin| not Vagrant.has_plugin? plugin }
if not plugins_to_install.empty?
  puts "Installing plugins: #{plugins_to_install.join(' ')}"
  if system "vagrant plugin install #{plugins_to_install.join(' ')}"
    exec "vagrant #{ARGV.join(' ')}"
  else
    abort "Installation of one or more plugins has failed. Aborting."
  end
end

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

  config.proxy.http     = "#{ENV['http_proxy']}"
  config.proxy.https    = "#{ENV['https_proxy']}"
  config.proxy.no_proxy = "localhost,127.0.0.1"

  config.vm.box = "centos/7"

  config.vm.provision "shell", privileged: true,
    inline: $script_to_install_ansible
end

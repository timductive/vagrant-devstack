# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.define :controller do |controller_config|

    # Every Vagrant virtual environment requires a box to build off of.
    controller_config.vm.box = "precise64"

    controller_config.vm.host_name = "controller"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    controller_config.vm.box_url = "http://files.vagrantup.com/precise64.box"

    # Assign this VM to a host-only network IP, allowing you to access it
    # via the IP. Host-only networks can talk to the host machine as well as
    # any other machines on the same network, but cannot be accessed (through this
    # network interface) by any external networks.
    controller_config.vm.network :hostonly, "172.16.0.201", :netmask => "255.255.0.0"

    # Customise the VM virtual hardware
    controller_config.vm.customize ["modifyvm", :id, "--memory", 2048]
    controller_config.vm.customize ["modifyvm", :id, "--cpus", 2]

    # Share a folder in which the python package cache will be exposed
    # Fill in there the packages if you can't wait for the packages download
    config.vm.share_folder "pip_cache", "/pip_cache", "pip_cache", :create => true
  
    # Execute the installation scripts (via SSH)
    controller_config.vm.provision :shell, :path => "devstack-bootstrap.sh"
  end

end

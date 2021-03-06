# Prototype vagrant configuration for an eZ Publish 5.1 box, using
# Ansible for provisioning.
#
# @author Filipe Dobreira <filipe.dobreira@cleverti.com>

Vagrant.configure("2") do |config|
  # CentOS 6.4, x64
  config.vm.box     = "centos-64-x64-vbox4210"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-64-x64-vbox4210.box"

  # Set the machine's hostname:
  config.vm.hostname = "ezp5.vagrant"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: "192.168.11.226"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Increase machine memory:
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # Enable Ansible as the provisioner for this machine:
  config.vm.provision :ansible do |ansible|
    ansible.inventory_file = "provisioning/hosts"
    ansible.playbook       = "provisioning/playbook.yml"
  end
end

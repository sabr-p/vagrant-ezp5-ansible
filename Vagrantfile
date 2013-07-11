# Prototype vagrant configuration for an eZ Publish 5.1 box, using
# Ansible for provisioning.
#
# @author Filipe Dobreira <filipe.dobreira@cleverti.com>

Vagrant.configure("2") do |config|
  # CentOS 6.4, x64
  config.vm.box     = "centos-64-x64-vbox4210"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-64-x64-vbox4210.box"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: "192.168.11.226"

  # Sync the ezpublish 5.x project root to a local folder
  # config.vm.synced_folder "sync", "/var/www", :nfs => true

  # Enable Ansible as the provisioner for this machine:
  config.vm.provision :ansible do |ansible|
    ansible.inventory_file = "provisioning/hosts"
    ansible.playbook       = "provisioning/playbook.yml"
  end
end

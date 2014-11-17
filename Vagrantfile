# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos6.5"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box" 

  config.vm.synced_folder "./", "/vagrant", create:true, :mount_options => ["dmode=777,fmode=777"]

  config.vm.network :private_network, ip: "192.168.33.11"
  config.vm.provision "ansible" do |ansible|
	  ansible.sudo = true
    ansible.ask_sudo_pass = true
    ansible.verbose = 'vvvv'
    ansible.playbook = "provisioning/local.yml"
    ansible.inventory_path = "provisioning/ansible_hosts"
    ansible.limit = 'local'
  end
end

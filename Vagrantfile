# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define :centos do |centos|
    centos.vm.box = "CentOS-6.5-x86_64-bento"
    centos.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box"
    centos.vm.hostname = "centos"
    centos.vm.box_check_update = false

    centos.vm.network :private_network, ip: "192.168.33.222"
    centos.ssh.forward_agent = true

    centos.vm.provider "virtualbox" do |vb|
      vb.gui = false

      vb.customize ["modifyvm", :id, "--memory", "384"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

    centos.vm.provision :ansible do |ansible|
      ansible.playbook = "site.yml"
      ansible.limit = "vagrant-centos"
      ansible.inventory_path = "vagrant.box"
      ansible.verbose = "vvv"
    end
  end

  config.vm.define :ubuntu do |ubuntu|
    ubuntu.vm.box = "Ubuntu-12.04-x86_64-bento"
    ubuntu.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-12.04_chef-provisionerless.box"
    ubuntu.vm.box_check_update = false
    ubuntu.vm.hostname = "ubuntu"

    ubuntu.vm.network :private_network, ip: "192.168.33.223"
    ubuntu.ssh.forward_agent = true

    ubuntu.vm.provider "virtualbox" do |vb|
      vb.gui = false

      vb.customize ["modifyvm", :id, "--memory", "384"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

    ubuntu.vm.provision :ansible do |ansible|
      ansible.playbook = "site.yml"
      ansible.limit = "vagrant-ubuntu"
      ansible.inventory_path = "vagrant.box"
      ansible.verbose = "vvv"
    end
  end

  config.vm.define :debian do |debian|
    debian.vm.box = "Debian-6-x86_64-bento"
    debian.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_debian-6.0.8_chef-provisionerless.box"
    debian.vm.box_check_update = false
    debian.vm.hostname = "debian"

    debian.vm.network :private_network, ip: "192.168.33.224"
    debian.ssh.forward_agent = true

    debian.vm.provider "virtualbox" do |vb|
      vb.gui = false

      vb.customize ["modifyvm", :id, "--memory", "384"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

    debian.vm.provision :ansible do |ansible|
      ansible.playbook = "site.yml"
      ansible.limit = "vagrant-debian"
      ansible.inventory_path = "vagrant.box"
      ansible.verbose = "vvv"
    end
  end


end

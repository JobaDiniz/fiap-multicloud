# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ## Escolha da Box (Imagem)
  config.vm.box = "ubuntu/bionic64"

  ## WORKSPACE
  config.vm.define 'multicloud' do |multicloud|
    multicloud.vm.hostname = "multicloud"

    # Configurações de Tamanho da VM
    multicloud.vm.provider "virtualbox" do |v|
      v.name = "multicloud"
      v.memory = 1024
      v.cpus = 2
    end

    # Instala o Ansible e faz as configurações da VM
    multicloud.vm.provision :ansible_local do |ansible|
        ansible.install_mode = "pip"
        ansible.version = "2.9.20"
        ansible.pip_install_cmd = "curl https://bootstrap.pypa.io/pip/2.7/get-pip.py | sudo python"
        #ansible.pip_install_cmd = "sudo apt-get install -y python3-distutils && curl -s https://bootstrap.pypa.io/get-pip.py | sudo python3"
        ansible.playbook = "playbook.yml"
        ansible.verbose  = true
        ansible.install  = true
        ansible.limit    = "all" 
        ansible.inventory_path = "inventory"
    end

  end

end

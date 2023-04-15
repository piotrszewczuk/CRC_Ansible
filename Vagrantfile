# Vagranfile for CRC Ansible Lab

Vagrant.configure("2") do |masterConfig|
  #VM1: Ansible Master Node
  masterConfig.vm.define "ansible-master" do |master|
    master.vm.box = "generic/debian11"
    master.vm.hostname = "ansible-master"
    master.vm.network :private_network, ip: "192.168.60.20"
    master.ssh.insert_key = false
    master.vm.provider "virtualbox" do |vMaster|
      vMaster.name = "ansible-master"
      vMaster.customize ["modifyvm", :id, "--memory", 2048]
      vMaster.customize ["modifyvm", :id, "--cpus", 2]
      vMaster.customize ["modifyvm", :id, "--groups", "/CRC_Ansible"]
    end
    master.vm.provision "shell", inline: <<-SHELL
      sudo apt-get install -y chrony vim 
      sudo systemctl enable --now chrony
      sudo echo "syntax on" >> /etc/vim/vimrc
      echo "192.168.60.10 node1.learntech.it node1" >> /etc/hosts
      echo "192.168.60.12 node2.learntech.it node2" >> /etc/hosts
      echo "192.168.60.14 node3.learntech.it node3" >> /etc/hosts
    SHELL
  end
end

Vagrant.configure("2") do |node1Config|
  #VM2: node1
  node1Config.vm.define "node1" do |node1|
    node1.vm.box = "generic/debian11"
    node1.vm.hostname = "node1"
    node1.vm.network "private_network", ip: "192.168.60.10"
    node1.vm.network "forwarded_port", guest:80, host: 80
    node1.vm.network "forwarded_port", guest:8888, host: 8888
    node1.ssh.insert_key = false
    node1.vm.provider "virtualbox" do |vNode1|
      vNode1.name = "node1"
      vNode1.customize ["modifyvm", :id, "--memory", 2048]
      vNode1.customize ["modifyvm", :id, "--cpus", 1]
      vNode1.customize ["modifyvm", :id, "--groups", "/CRC_Ansible"]
    end
    node1.vm.provision "shell", inline: <<-SHELL
      sudo apt-get install -y chrony curl
      sudo systemctl enable --now chrony
      echo "192.168.60.10 node1.learntech.it node1" >> /etc/hosts
      echo "192.168.60.12 node2.learntech.it node2" >> /etc/hosts
      echo "192.168.60.14 node3.learntech.it node3" >> /etc/hosts
    SHELL
  end
end

Vagrant.configure("2") do |node2Config|
  #VM3: Node2
  node2Config.vm.define "node2" do |node2|
    node2.vm.box = "generic/debian11"
    node2.vm.hostname = "node2"
    node2.vm.network :private_network, ip: "192.168.60.12"
    node2.ssh.insert_key = false
    node2.vm.provider "virtualbox" do |vNode2|
      vNode2.name = "node2"
      vNode2.customize ["modifyvm", :id, "--memory", 2048]
      vNode2.customize ["modifyvm", :id, "--cpus", 1]
      vNode2.customize ["modifyvm", :id, "--groups", "/CRC_Ansible"]
    end
    node2.vm.provision "shell", inline: <<-SHELL
      sudo apt-get install -y chrony curl
      sudo systemctl enable --now chrony
      echo "192.168.60.10 node1.learntech.it node1" >> /etc/hosts
      echo "192.168.60.12 node2.learntech.it node2" >> /etc/hosts
      echo "192.168.60.14 node3.learntech.it node3" >> /etc/hosts
    SHELL
  end
end

Vagrant.configure("2") do |node3Config|
  #VM4: Node3
  node3Config.vm.define "node3" do |node3|
    node3.vm.box = "generic/debian11"
    node3.vm.hostname = "node3"
    node3.vm.network :private_network, ip: "192.168.60.14"
    node3.ssh.insert_key = false
    node3.vm.provider "virtualbox" do |vNode3|
      vNode3.name = "node3"
      vNode3.customize ["modifyvm", :id, "--memory", 2048]
      vNode3.customize ["modifyvm", :id, "--cpus", 1]
      vNode3.customize ["modifyvm", :id, "--groups", "/CRC_Ansible"]
    end
    node3.vm.provision "shell", inline: <<-SHELL
      sudo apt-get install -y chrony curl
      sudo systemctl enable --now chrony
      echo "192.168.60.10 node1.learntech.it node1" >> /etc/hosts
      echo "192.168.60.12 node2.learntech.it node2" >> /etc/hosts
      echo "192.168.60.14 node3.learntech.it node3" >> /etc/hosts
    SHELL
  end
end

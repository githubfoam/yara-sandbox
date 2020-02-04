# -*- mode: ruby -*-
# vi: set ft=ruby :
$docker_compose_script = <<SCRIPT
#Install clamav python3
apt-get update && apt-get -y install python3 python3-pip clamav
cd /tmp && git clone https://github.com/Hestat/lw-yara.git
clamscan -ir -l /tmp/scanresults.txt -d /tmp/lw-yara/lw-rules_index.yar -d /tmp/lw-yara/lw.hdb /home
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.define "control01" do |webtier|
      webtier.vm.box = "bento/ubuntu-19.04"
      webtier.vm.hostname = "control01"
      webtier.vm.network "private_network", ip: "192.168.45.10"
      webtier.vm.provider "virtualbox" do |vb|
          vb.name = "control01"
          vb.gui = false
          vb.memory = "512"
          vb.cpus = 1
      end
      webtier.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.version = "2.9.4"
      ansible.playbook = "deploy.yml"
      end
      webtier.vm.provision "shell", inline: <<-SHELL
      hostnamectl set-hostname control01
      echo "192.168.45.10 control01.local control01" |sudo tee -a /etc/hosts
      echo "192.168.45.11 control02.local control02" |sudo tee -a /etc/hosts
      echo "192.168.45.12 control03.local control03" |sudo tee -a /etc/hosts
      echo "name: nameserver, ip: 8.8.8.8 " |sudo tee -a /etc/resolv.conf
      echo "===================================================================================="
                                hostnamectl status
      echo "===================================================================================="
      echo "         \   ^__^                                                                  "
      echo "          \  (oo)\_______                                                          "
      echo "             (__)\       )\/\                                                      "
      echo "                 ||----w |                                                         "
      echo "                 ||     ||                                                         "
      SHELL
  end

  config.vm.define "control02" do |webtier|
      webtier.vm.box = "bento/centos-7.7"
      webtier.vm.hostname = "control02"
      webtier.vm.network "private_network", ip: "192.168.45.11"
      webtier.vm.provider "virtualbox" do |vb|
          vb.name = "control02"
          vb.gui = false
          vb.memory = "512"
          vb.cpus = 1
      end
      webtier.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.version = "2.9.2"
      ansible.playbook = "deploy.yml"
      end
      webtier.vm.provision "shell", inline: <<-SHELL
      hostnamectl set-hostname control02
      echo "192.168.45.10 control01.local control01" |sudo tee -a /etc/hosts
      echo "192.168.45.11 control02.local control02" |sudo tee -a /etc/hosts
      echo "192.168.45.12 control03.local control03" |sudo tee -a /etc/hosts
      echo "name: nameserver, ip: 8.8.8.8 " |sudo tee -a /etc/resolv.conf
      SHELL
      webtier.vm.provision "shell", inline: <<-SHELL
      echo "===================================================================================="
                                hostnamectl status
      echo "===================================================================================="
      echo "         \   ^__^                                                                  "
      echo "          \  (oo)\_______                                                          "
      echo "             (__)\       )\/\                                                      "
      echo "                 ||----w |                                                         "
      echo "                 ||     ||                                                         "
      SHELL
  end


  config.vm.define "control03" do |webtier|
      webtier.vm.box = "bento/centos-7.7"
      webtier.vm.hostname = "control03"
      webtier.vm.network "private_network", ip: "192.168.45.12"
      webtier.vm.provider "virtualbox" do |vb|
          vb.name = "control03"
          vb.gui = false
          vb.memory = "1024"
          vb.cpus = 1
      end
      webtier.vm.provision "shell", inline: <<-SHELL
      hostnamectl set-hostname control03
      echo "192.168.45.10 control01.local control01" |sudo tee -a /etc/hosts
      echo "192.168.45.11 control02.local control02" |sudo tee -a /etc/hosts
      echo "192.168.45.12 control03.local control03" |sudo tee -a /etc/hosts
      echo "name: nameserver, ip: 8.8.8.8 " |sudo tee -a /etc/resolv.conf
      SHELL
      webtier.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.version = "2.9.2"
      ansible.playbook = "deploy_RedHat.yml"
      end
      webtier.vm.provision "shell", inline: <<-SHELL
      echo "===================================================================================="
                                hostnamectl status
      echo "===================================================================================="
      echo "         \   ^__^                                                                  "
      echo "          \  (oo)\_______                                                          "
      echo "             (__)\       )\/\                                                      "
      echo "                 ||----w |                                                         "
      echo "                 ||     ||                                                         "
      SHELL
  end


end

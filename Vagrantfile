# -*- mode: ruby -*-
# vi: set ft=ruby :
$docker_compose_script = <<SCRIPT
#Build and install an RPM
#https://sylabs.io/guides/3.5/admin-guide/installation.html
export VERSION=3.5.2 && # adjust this as necessary \
cd /opt && wget https://github.com/sylabs/singularity/releases/download/v${VERSION}/singularity-${VERSION}.tar.gz  && \
# rpmbuild -tb singularity-${VERSION}.tar.gz
# sudo rpm -ivh ~/rpmbuild/RPMS/x86_64/singularity-$VERSION-1.el7.x86_64.rpm && \
# rm -rf ~/rpmbuild singularity-$VERSION*.tar.gz
SCRIPT
$docker_compose_script = <<SCRIPT
# Get Docker Engine - Community for CentOS
# https://docs.docker.com/install/linux/docker-ce/centos/
sudo yum remove docker \
docker-client \
docker-client-latest \
docker-common \
docker-latest \
docker-latest-logrotate \
docker-logrotate \
docker-engine
sudo yum install -y yum-utils \
device-mapper-persistent-data \
lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install -y docker-ce \
docker-ce-cli \
containerd.io
sudo systemctl enable docker
sudo systemctl start docker && sudo docker --version
sudo usermod -aG docker vagrant # add user to the docker group
# Install Docker Compose
# https://docs.docker.com/compose/install/
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose && sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
sudo docker-compose --version
sudo yum install traceroute -y
hostnamectl status
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
      apt-get update && apt-get -y install python3 python3-pip clamav
      cd /tmp && git clone https://github.com/Hestat/lw-yara.git
      clamscan -ir -l /tmp/scanresults.txt -d /tmp/lw-yara/lw-rules_index.yar -d /tmp/lw-yara/lw.hdb /home
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
      # webtier.vm.provision "shell", inline: $docker_compose_script, privileged: false
      webtier.vm.provision "shell", inline: <<-SHELL
      # yum install epel-release -y && yum install python-pip git -y && pip --version # hpccm requirements
      # pip install hpccm && pip install --upgrade pip && pip --version #install hpccm
      # git clone https://github.com/NVIDIA/hpc-container-maker.git && cd hpc-container-maker
      # hpccm --recipe recipes/examples/basic.py --format docker > Dockerfile.basic
      # docker build . -t basic:docker --file Dockerfile.basic
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
      # webtier.vm.provision "shell", inline: $docker_compose_script, privileged: false
      webtier.vm.provision "shell", inline: <<-SHELL
      # yum install epel-release -y && yum install python-pip git -y && pip --version # hpccm requirements
      # pip install hpccm && pip install --upgrade pip && pip --version #install hpccm
      # git clone https://github.com/NVIDIA/hpc-container-maker.git && cd hpc-container-maker
      # hpccm --recipe recipes/examples/basic.py --format docker > Dockerfile.basic
      # hpccm --recipe recipes/examples/basic.py --format singularity > Singularity.basic
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

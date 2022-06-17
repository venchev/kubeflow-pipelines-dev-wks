# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "mrysbekov/ubuntu2204"
  config.vm.hostname = "kfdev"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 8
    vb.name = "KubeFlow Dev Station"
end

 config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update && sudo apt-get upgrade -y
     sudo apt-get install -y vim nano mc lynx git nmap wget curl net-tools htop snapd snap
     sudo snap refresh
     sudo snap install juju --classic
     sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
     echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
     sudo apt update
     apt-cache policy docker-ce
     sudo apt install docker-ce -y
     sudo systemctl enable docker
     sudo systemctl start docker
     sudo usermod -aG docker ${USER}
     sudo reboot
 SHELL

end

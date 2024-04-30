# -*- mode: ruby -*-
# vim: set ft=ruby :
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure(2) do |config|
config.vm.box = "centos/7"
config.vm.box_version = "1.0.0"
config.vm.provider "virtualbox" do |v|
v.memory = 256
v.cpus = 1
end
config.vm.define "dockernginx" do |dockernginx|
dockernginx.vm.hostname = "dockernginx"
dockernginx.vm.provision "shell", inline: <<-SHELL
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce docker-ce-cli containerd.io
systemctl enable docker
systemctl start docker
curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
SHELL
end
end
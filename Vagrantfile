$script = <<SCRIPT
set -x

sudo apt-get update > /dev/null
sudo apt-get install git vim-common -y
echo "deb http://ftp.debian.org/debian jessie-backports main" >> /etc/apt/sources.list
sudo apt-get update > /dev/null
sudo apt-get -t jessie-backports install ansible -y > /dev/null

cp /vagrant/setup.yml /vagrant/setup_vagrant.yml
cp /vagrant/vars.yml /vagrant/vars_vagrant.yml

sed -i "s/user:.*/user: vagrant/g" /vagrant/vars_vagrant.yml
sed -i "s/vars.yml*/vars_vagrant.yml/g" /vagrant/setup_vagrant.yml

ansible-playbook /vagrant/setup_vagrant.yml

rm /vagrant/vars_vagrant.yml
rm /vagrant/setup_vagrant.yml
SCRIPT

Vagrant.configure("2") do |config|
  # https://atlas.hashicorp.com/boxcutter/boxes/ubuntu1604-desktop
  config.vm.box = "boxcutter/debian8" # jessie

  config.vm.provision "shell", inline: $script
  config.vm.hostname = "debian-lean"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "2048"
  end
end


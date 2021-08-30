$script = <<-SCRIPT
apt-get update
apt-get install git docker docker-compose -y
systemctl enable docker && systemctl start docker
chown -R vagrant:vagrant /media
git clone https://github.com/RomainAmardeil/download-box.git
chown -R vagrant:vagrant download-box
cd download-box
docker-compose up -d
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provision "shell", inline: $script
  config.vm.synced_folder "./DownloadContent", "/media"
  config.vm.network "public_network", ip: "192.168.8.50"
end

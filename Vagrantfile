Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update -y
    apt-get install -y docker.io
    systemctl start docker
    systemctl enable docker
    usermod -aG docker vagrant
  SHELL

  config.vm.define "manager" do |m|
    m.vm.hostname = "swarm-manager"
    m.vm.network "private_network", ip: "192.168.56.10"
    m.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end

  config.vm.define "worker1" do |w|
    w.vm.hostname = "swarm-worker1"
    w.vm.network "private_network", ip: "192.168.56.11"
    w.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end
  end

  config.vm.define "worker2" do |w|
    w.vm.hostname = "swarm-worker2"
    w.vm.network "private_network", ip: "192.168.56.12"
    w.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end
  end
end

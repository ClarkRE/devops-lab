Vagrant.configure("2") do |config|
  config.vm.provider "vmware_desktop" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  # Control Node
  config.vm.define "control-node" do |node|
    node.vm.box = "bento/ubuntu-22.04"
    node.vm.hostname = "control-node"
    node.vm.network "private_network", ip: "192.168.56.10"
    node.vm.provision "shell", path: "scripts/install_docker.sh"
    node.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y ansible terraform
    SHELL
  end

  # Worker Node
  config.vm.define "worker-node" do |node|
    node.vm.box = "bento/ubuntu-22.04"
    node.vm.hostname = "worker-node"
    node.vm.network "private_network", ip: "192.168.56.11"
    node.vm.provision "shell", path: "scripts/install_docker.sh"
  end
end

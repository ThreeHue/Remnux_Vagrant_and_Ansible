Vagrant.configure("2") do |config|
  config.vm.box = "remnux"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "remnux-vm"
    vb.memory = 4096
    vb.cpus = 2
    vb.gui = true
  end

  config.vm.network "private_network", type: "dhcp"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision.yml"
  end
end

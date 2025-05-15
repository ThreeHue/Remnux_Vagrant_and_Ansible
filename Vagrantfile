Vagrant.configure("2") do |config|
  config.vm.box = "remnux"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "remnux-vm"
    vb.memory = 4096
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--storagectl", "SATA Controller", "--portcount", 2]
    vb.customize ["createhd", "--filename", "extra_disk.vdi", "--size", 20480] # 20 GB extra
    vb.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", 1, "--device", 0, "--type", "hdd", "--medium", "extra_disk.vdi"]
  end

  config.vm.network "private_network", type: "dhcp"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision.yml"
  end
end

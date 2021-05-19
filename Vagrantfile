## Info

Vagrant.configure("2") do |masterConfig|
  #VM1: rancher
  masterConfig.vm.define "rancher" do |rancher|
    rancher.vm.box = "opensuse/Leap-15.2.x86_64"
    rancher.vm.hostname = "rancher"
    rancher.vm.network "private_network", ip: "192.168.10.10"
    rancher.vm.network "forwarded_port", guest: 80, host: 80
    rancher.vm.network "forwarded_port", guest: 443, host: 443
    rancher.ssh.insert_key = false
    rancher.vm.provider "libvirt" do |vMaster|
      vMaster.memory = 4096
      vMaster.cpus = 4
    end
    rancher.vm.provider "virtualbox" do |vMaster|
      vMaster.name = "SUSE_Rancher"
      vMaster.customize ["modifyvm", :id, "--memory", 4096]
      vMaster.customize ["modifyvm", :id, "--cpus", 4]
      vMaster.customize ["modifyvm", :id, "--groups", "/SUSE_Rancher"]
    end
    rancher.vm.provision "shell", inline: <<-SHELL
      zypper ref
      zypper in -y -t pattern yast2_basis
      zypper in -y docker
      systemctl enable --now docker      
    SHELL
  end
  #VM2 worker
  masterConfig.vm.define "worker" do |worker|
    worker.vm.box = "opensuse/Leap-15.2.x86_64"
    worker.vm.hostname = "worker"
    worker.vm.network "private_network", ip: "192.168.10.11"
    worker.ssh.insert_key = false
    worker.vm.provider "libvirt" do |vworker|
      vworker.memory = 8192
      vworker.cpus = 4
    end
    worker.vm.provider "virtualbox" do |vworker|
      vworker.name = "SUSE_Worker"
      vworker.customize ["modifyvm", :id, "--memory", 8192]
      vworker.customize ["modifyvm", :id, "--cpus", 4]
      vworker.customize ["modifyvm", :id, "--groups", "/SUSE_Rancher"]
    end
    worker.vm.provision "shell", inline: <<-SHELL
      zypper ref
      zypper in -y -t pattern yast2_basis
      zypper in -y docker
      systemctl enable --now docker      
    SHELL
  end

end

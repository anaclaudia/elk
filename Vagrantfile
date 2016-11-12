Vagrant.configure("2") do |config|
  
  config.vm.define "elk" do |elk|
    elk.vm.box = "bento/ubuntu-14.04"
    elk.vm.hostname = "elk"
    elk.vm.network "forwarded_port", guest: 80, host: 8080
    elk.vm.network "private_network", ip: "192.168.33.10"
    elk.vm.synced_folder ".", "/vagrant"
    elk.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "main.yml"
      ansible.verbose = true
      ansible.install = true
    end
  end
  
  config.vm.define "web" do |web|
    web.vm.box = "bento/ubuntu-14.04"
    web.vm.hostname = "nginx"
    web.vm.network "private_network", ip: "192.168.33.11"
    web.vm.synced_folder ".", "/vagrant"
    web.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "web.yml"
      ansible.verbose = true
      ansible.install = true
    end
  end

end

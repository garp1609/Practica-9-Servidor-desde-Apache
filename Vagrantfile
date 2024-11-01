Vagrant.configure("2") do |config|
  # Configuración para las máquinas web1, web2 y nginx
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/jammy64"
    web1.vm.network "private_network", ip: "192.168.33.10"
    web1.vm.synced_folder "./src", "/var/www/html"
    web1.vm.provision "shell", inline: "sudo apt update && sudo apt install -y ansible"
    web1.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "apache.yml"
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/jammy64"
    web2.vm.network "private_network", ip: "192.168.33.11"
    web2.vm.synced_folder "./src", "/var/www/html"
    web2.vm.provision "shell", inline: "sudo apt update && sudo apt install -y ansible"
    web2.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "apache.yml"
    end
  end

  config.vm.define "nginx" do |nginx|
    nginx.vm.box = "ubuntu/jammy64"
    nginx.vm.network "private_network", ip: "192.168.33.12"
    nginx.vm.provision "shell", inline: "sudo apt update && sudo apt install -y ansible"
    nginx.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "nginx.yml"
    end
  end
end
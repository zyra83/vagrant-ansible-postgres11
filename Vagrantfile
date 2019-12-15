Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.provision "shell" do |s|
  #   ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
  #   s.inline = <<-SHELL
  #     echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
  #     echo #{ssh_pub_key} >> /root/.ssh/authorized_keys 
  #     # sudo apt-get update
  #     # sudo apt-get install -y python
  #   SHELL
  # end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "install.yml"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 1
  end  
end

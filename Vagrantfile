Vagrant.configure("2") do |config|
  # base configuration for all boxes
  config.vm.box = "centos/7"
  # config.vm.provision "shell", inline: <<-SHELL
  # apt-get update
  # apt-get -y upgrade
  # SHELL

  # create haproxy box
  config.vm.define "soufe1", primary: true do |hp|
    hp.vm.network :private_network, ip: "192.168.56.15"
    # hp.vm.network "forwarded_port", guest: 22, host: 2222
    hp.vm.network "forwarded_port", guest: 2222, host: 2222
  end

  # create prometheus and grafana boxes
  config.vm.define "soube2" do |hp|
    hp.vm.network :private_network, ip: "192.168.56.16"
    #hp.vm.network "forwarded_port", guest:25 , host: 5555
    hp.vm.network "forwarded_port", guest:5555 , host: 5555
  end

  # provision
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "roles/sou_podman/tasks/main.yml"
  end
end


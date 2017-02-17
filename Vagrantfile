
Vagrant.configure("2") do |config|

	config.vm.define "box1" do |box1|
		box1.vm.box="ubuntu/trusty64"
		box1.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"
		box1.vm.network :private_network, ip: "192.168.10.125"
		box1.vm.provider :virtualbox do |v|
			v.customize ["modifyvm", :id, "--memory", 1020]
		box1.vm.provision "shell", inline: <<-SHELL
			sudo apt-get update
			SHELL
		end
	end

	config.vm.define "box2" do |box2|
		box2.vm.box="scotch/box"
		box2.vm.network :forwarded_port, guest: 22, host: 10222, id: "ssh"
		box2.vm.network :private_network, ip: "192.168.10.150"
		box2.vm.provision "shell", inline: <<-SHELL
			sudo apt-get update
			sudo apt-get install -y nginx
			SHELL
		end
	end

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	config.vm.box = "centos64"
	config.vm.network :private_network, ip: "192.168.34.10"
	config.vm.network :forwarded_port, guest: 80, host: 8099

	config.vm.provision :chef_solo do |chef|
		chef.cookbooks_path = "."
		chef.roles_path = "roles"
		chef.add_role "vagrant"
	end

	config.vm.provider :virtualbox do |vb|
		vb.customize ["modifyvm", :id, "--rtcuseutc", "on", "--memory", "2048", "--cpus", "2", "--natdnshostresolver1", "on"]
	end

end

# vim:set syntax=ruby ts=4 sw=4:
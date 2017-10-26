[
  { :name => "vagrant-reload", :version => ">= 0" },
  { :name => "vagrant-vbguest", :version => ">= 0.15.0" }
].each do |plugin|

  if not Vagrant.has_plugin?(plugin[:name], plugin[:version])
    raise "#{plugin[:name]} #{plugin[:version]} is required. Please run `vagrant plugin install #{plugin[:name]}`"
  end
end


Vagrant.configure("2") do |config|

	config.vm.box = "v0rtex/xenial64"

	# setup vagrant VM with port forwarding and folder sharing
	config.vm.box = "v0rtex/xenial64"
	config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
	config.vm.network "forwarded_port", guest: 8000, host: 8000, host_ip: "127.0.0.1"
	
	# first parameter is host machine folder, 2nd parameter is VM folder
	config.vm.synced_folder "D:/Virtual Box  - Shared Files", "/home/vagrant/Downloads"
	
	config.vm.provision :reload

	# Create defualt installation for Ubuntu machine
	config.vm.provision "shell", run: "once", inline: <<-SHELL	
		echo "[vagrant provisioning] Installing Python3 specific dependencies"
		sudo apt-get -q install -y python3-pip
		yes | pip3 install --upgrade pip

		yes | pip3 install virtualEnv
		mkdir ~/.virtualenvs
			
		echo "making python3 and pip3 the default"
		echo "alias python=python3" >> ~/.bash_aliases
		source ~/.bash_aliases
		sudo ln -s /usr/bin/pip3 /usr/bin/pip
		
		echo "updating Ubuntu"
		sudo apt-get -q -y update
		sudo apt-get -q -y upgrade

		sudo rm /boot/grub/menu.lst
        sudo update-grub-legacy-ec2 -y
        sudo dpkg --configure -a
        sudo apt-get dist-upgrade -y
        sudo reboot

	SHELL
end

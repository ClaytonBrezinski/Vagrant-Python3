Vagrant.configure("2") do |config|

  config.vm.box = "v0rtex/xenial64"

  # setup vagrant VM with port forwarding and folder sharing
	config.vm.box = "v0rtex/xenial64"
	config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
	config.vm.network "forwarded_port", guest: 8000, host: 8000, host_ip: "127.0.0.1"
	
	# first parameter is host machine folder, 2nd parameter is VM folder
	config.vm.synced_folder "D:\Virtual Box  - Shared Files", "~/downloads"
  
	#Create defualt installation for Ubuntu machine
	config.vm.provision :shell, inline: <<-SHELL
		echo "updating Ubuntu"
		sudo apt-get -q update
		sudo apt-get -q upgrade
		
		echo "making python3 and pip3 the default"
		echo "alias python=python3" >> ~/.bash_aliases
		source ~/.bash_aliases
		sudo ln -s /usr/bin/pip3 /usr/bin/pip
		
		echo "[vagrant provisioning] Installing Python3 specific dependencies"
		apt-get -q install -y python3-pip
		
		pip3 install virtualEnv
		mkdir ~/.virtualenvs
end

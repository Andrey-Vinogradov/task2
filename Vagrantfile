

# task2
Vagrant.configure("2") do |config|
 config.vm.box = "bento/centos-7.2"
 config.vm.box_check_update = false

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = "512"
  end

  config.vm.define "vbox1" do |v1|
    v1.vm.hostname = "v1"
    v1.vm.network "private_network", ip: "192.168.56.111"
    v1.vm.provision "shell", inline: <<-SHELL
    yum install git -y
	sudo yum install mc -y
    git config --global user.name "Andrei Vinahradau"
    git config --global user.email "veter3003g@gmail.com"
	mkdir -p /git/task2
	git clone https://github.com/Andrey-Vinogradov/task2.git /git/task2
	cd /git/task2
	git checkout master
	cat /git/task2/test.txt
	echo -e "192.168.56.222 v2\n192.168.56.111 v1\n127.0.0.1 v1\n127.0.0.1 localhost" > /etc/hosts
 SHELL
  end

  config.vm.define "vbox2" do |v2|
    v2.vm.hostname = "v2"
    v2.vm.network "private_network", ip: "192.168.56.222"
    v2.vm.provision "shell", inline: <<-SHELL
	echo -e "192.168.56.222 v2\n192.168.56.111 v1\n127.0.0.1 v1\n127.0.0.1 localhost" > /etc/hosts
 SHELL
  end
end
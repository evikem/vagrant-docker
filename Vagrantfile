Vagrant.configure(2) do |config|
 
  config.vm.define "ace" do |r|
    r.vm.box = "ubuntu/trusty64"

    r.vm.provision :shell, path: "bootstrap.sh"

    r.vm.provision "docker" do |d|
      d.build_image '-t "javabase" /vagrant/java_base'
    end

	r.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", rebuild: true, run: "always"
	
    r.vm.network :forwarded_port, guest: 8080, host: 9080
    r.vm.network :forwarded_port, guest: 8081, host: 9081
    r.vm.network :forwarded_port, guest: 8082, host: 9082
    r.vm.network :forwarded_port, guest: 1089, host: 9090
    r.vm.network :forwarded_port, guest: 80, host: 9080
    r.vm.network "private_network", ip: "192.168.0.32"

    r.vm.provider "virtualbox" do |vb|
       vb.customize ["modifyvm", :id, "--usb","off", "--vram",64]
       vb.gui = false
       vb.memory = 8192
       vb.cpus = 4
    end
	
  end
  
  config.vm.provision "file", source: "D:/vagrant/nodes", destination: "nodes"
  config.vm.provision "file", source: "D:/vagrant/credentials.xml", destination: "credentials.xml"
  
end

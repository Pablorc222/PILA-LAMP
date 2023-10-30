config.vm.define "PabloRdgzApache" do |apache|
  apache.vm.box = "ubuntu/xenial64
  apache.vm.network "private_network" , type: "dhcp"
   apache.vm.provider "virtualbox" do |vb|
     vb.memory = "512"
config.vm.provision "shell", path: "script1.sh"
end 
end
config.vm.define "PabloRdgzMysql" do |mysql|
  apache.vm.box = "ubuntu/xenial64
  apache.vm.network "private_network" , type: "dhcp"
   apache.vm.provider "virtualbox" do |vb|
     vb.memory = "512"
config.vm.provision "shell", path: "script2.sh"
end 
end

# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    
     # General Vagrant VM configuration.
     config.vm.box = "ubuntu/jammy64"
     config.ssh.insert_key = false
     config.vm.synced_folder ".", "/vagrant", disabled: true
     config.vm.provider :virtualbox do |v|
        v.memory = 1024
        v.cpus = 2
        v.linked_clone = true
     end
    # Gms1
    config.vm.define "gms1" do |app|
        app.vm.hostname = "gms1.test"
        app.vm.network :private_network, ip: "192.168.56.4"
    end
    # Panel1
    config.vm.define "panel1" do |app|
        app.vm.hostname = "panel1.test"
        app.vm.network :private_network, ip: "192.168.56.5"
    end 
end
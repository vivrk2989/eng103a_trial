
Vagrant.configure("2") do |config|
 config.vm.define "app" do |app|
 # creating a virtual machine ubuntu
  app.vm.box = "ubuntu/xenial64"
 # creating a private network with ip
  app.vm.network "private_network", ip: "192.168.10.100"

 # Synced app folder     localhost path, path for vm
  app.vm.synced_folder ".", "/home/vagrant/app"
                          # . means everything from current location
 # Synced environment folder 
  app.vm.synced_folder "environment", "/home/vagrant/environment"
 # Provisioning        runs the shell script, from where
  app.vm.provision "shell", path: "provisionapp/provision.sh", privileged: false 
 end

 # creating mongodb vm
 config.vm.define "db" do |db|
  # creating a virtual machine ubuntu for db
  db.vm.box = "ubuntu/xenial64"  
  # creating a private network with ip
  db.vm.network "private_network", ip: "192.168.10.150"
  # syncing db folder to the db vm
  db.vm.synced_folder ".", "/home/vagrant/db"
  # creating a provision file that automates installation of dependencies
  db.vm.provision "shell", path: "provisiondb/provision.sh", privileged: false


 end

end
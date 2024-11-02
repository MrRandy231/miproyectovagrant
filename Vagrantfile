# Configuración de Vagrantfile para crear una máquina virtual con Apache
Vagrant.configure("2") do |config|
  
    # Selección de la imagen base (Ubuntu en este caso)
    config.vm.box = "ubuntu/bionic64"
    
    # Configuración de memoria RAM y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configuración de la red para acceder al servidor web
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Compartir el directorio local 'paginas_web' con Apache en la máquina virtual
    config.vm.synced_folder "./paginas_web", "/var/www/html"
    
    # Configuración para instalar Apache automáticamente
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  
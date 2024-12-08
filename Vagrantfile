# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.vm.define "pedro" do |pedro|
    # Configuración de la máquina virtual
    pedro.vm.box = "debian/bookworm64"
    pedro.vm.network "private_network", ip: "192.168.57.103"


    # Aprovisionamiento de la máquina
    pedro.vm.provision "shell", inline: <<-SHELL
      # Actualización del sistema e instalación de paquetes
      apt-get update -y
      apt-get install -y nginx openssl apache2-utils

      
      # Crear directorios para los sitios web
      mkdir -p /var/www/pedro/html
      mkdir -p /var/www/perfectweb/html
    SHELL
  end
end

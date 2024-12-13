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
    
      # Crear directorios para los sitios web
      mkdir -p /var/www/pedro/html
      mkdir -p /var/www/perfectweb/html

      # Clonar el repositorio en /var/www/pedro/html
      git clone https://github.com/cloudacademy/static-website-example /var/www/pedro/html

      # Copiar el contenido del sitio perfecto desde /vagrant/html
      cp -r /vagrant/html/* /var/www/perfectweb/html/
      
      # Configurar permisos
      chown -R www-data:www-data /var/www/pedro
      chmod -R 755 /var/www/pedro
      chown -R www-data:www-data /var/www/perfectweb
      chmod -R 755 /var/www/perfectweb

      # Configuración de NGINX
      cp /vagrant/pedro /etc/nginx/sites-available/pedro
      ln -sf /etc/nginx/sites-available/pedro /etc/nginx/sites-enabled/

      cp /vagrant/perfectweb /etc/nginx/sites-available/perfectweb
      ln -sf /etc/nginx/sites-available/perfectweb /etc/nginx/sites-enabled/

      # Autenticación básica para 'perfectweb'
      cp /vagrant/.htpasswd /etc/nginx/.htpasswd

      # Crear un certificado autofirmado
      openssl req -x509 -nodes -days 365 -newkey rsa:2048 keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt -subj "/C=US/ST=State/L=City/O=Organization/OU=OrgUnit/CN=localhost"
      
      
      
      SHELL
  end
end

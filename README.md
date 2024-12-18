# DEAW-DUAL-Prac6

# Practica 6

# Estrutura de directorios

```
.
├── Vagrantfile
├── html/                     # Archivos del sitio
│   └── logo.png              # Imagen para pruebas de descarga
├── pedro                     # Configuración NGINX para el sitio 'pedro'
├── perfectweb                # Configuración NGINX para el sitio 'perfectweb'
├── .htpasswd                 # Archivo para autenticación básica
├── error_pages/              # Páginas personalizadas de error
│   └── 404.html
```

# Configuración del Proyecto

1. Estructura de los Sitios Web
   - Sitio pedro:
     - Sirve contenido estático clonado de Static Website Example.
     - Accesible desde: `http://192.168.57.103`.
   - Sitio perfectweb:
     - Sirve contenido desde la carpeta html/.
     - Protegido con autenticación básica (usuario y contraseña).
     - Accesible desde: http://192.168.57.103/perfectweb.
2. Características de Seguridad
   - Certificado SSL/TLS:
     - Se genera automáticamente un certificado autofirmado durante el aprovisionamiento.
     - Puedes reemplazarlo con uno de Let’s Encrypt para mayor seguridad.
   - Autenticación Básica:
     - Protege el sitio perfectweb con un archivo .htpasswd.
3. Páginas Personalizadas
   - Página de error personalizada (404.html):
     - Se muestra cuando un recurso no existe.

# Uso del Proyecto

1. Iniciar el Servidor
   Levanta la máquina virtual con el siguiente comando:

```
vagrant up
```

Esto:

- Crea la máquina virtual con Debian.
- Configura NGINX para servir los sitios pedro y perfectweb.
- Instala los certificados SSL/TLS autofirmados.

2. Acceso a los Sitios Web

   - Sitio pedro:
     - URL: `http://192.168.57.103`.
   - Sitio perfectweb:
     - URL: `http://192.168.57.103/perfectweb`.
   - Credenciales para acceso:
     - Usuario: admin.
     - Contraseña: definida en .htpasswd.

3. Acceso SSH a la Máquina
   Conéctate a la máquina virtual para administrar directamente:

```
vagrant ssh pedro
```

4. Apagar o Eliminar la Máquina Virtual
   - Apagar la máquina:
   ```
    vagrant halt pedro
   ```
   - Eliminar la máquina:
   ```
   vagrant destroy pedro
   ```

# Personalización

1. Actualizar Certificados SSL
   Para reemplazar el certificado autofirmado con Let’s Encrypt, sigue esta guía.

2. Configuración de NGINX
   Modifica los archivos de configuración (pedro y perfectweb) para personalizar el comportamiento de los sitios.

3. Cambiar Credenciales de Autenticación
   Genera un nuevo archivo .htpasswd con las credenciales que desees:

```
htpasswd -c .htpasswd admin
```

# Resolución de Problemas

1. Páginas no Accesibles

- Verifica que los puertos 80 y 443 están abiertos en tu firewall/router.
- Asegúrate de que NGINX está corriendo:

```
sudo systemctl status nginx
```

2. Logs de NGINX
   Revisa los registros para identificar errores:

```
sudo tail -f /var/log/nginx/error.log
```

3. Conexión por HTTPS Insegura
   Si usas el certificado autofirmado, los navegadores mostrarán un aviso de seguridad. Puedes ignorarlo o instalar un certificado válido de Let’s Encrypt.

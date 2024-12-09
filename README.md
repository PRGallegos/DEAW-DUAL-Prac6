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


# RA3_1

## Introduction [INTRO](URL_TASKS)

Este documento proporciona una guía para completar las tareas relacionadas con RA3_1.

## Tasks

* [TASK_1](#URL_TASK_1): Implementación de seguridad en Apache
* [TASK_2](#URL_TASK_2): Gestión de contenedores Docker

## Task_1: Implementación de seguridad en Apache

### Introducción

En esta tarea, se aplicarán medidas de seguridad en un servidor Apache mediante la configuración de **Content Security Policy (CSP)** y la activación de módulos de seguridad.

![Configuración Apache](URL_IMG)

### Pasos

Ejecuta los siguientes comandos para configurar la seguridad en Apache:

```sh
# Habilitar el módulo de cabeceras
sudo a2enmod headers

# Reiniciar el servicio Apache
sudo systemctl restart apache2

# Aplicar política CSP
echo '<IfModule mod_headers.c>
    Header set Content-Security-Policy "default-src '\''self'\''; img-src *; media-src media1.com media2.com; script-src userscripts.example.com;"
</IfModule>' | sudo tee /etc/apache2/conf-available/security.conf

# Habilitar configuración de seguridad
sudo a2enconf security
sudo systemctl restart apache2
```

## Task_2: Gestión de contenedores Docker

### Introducción

En esta tarea, se trabajará con contenedores Docker para ejecutar y administrar aplicaciones de manera eficiente.

### Comandos útiles

- **Detener todos los contenedores en ejecución:**
  ```sh
  docker stop $(docker ps -aq)
  ```

- **Eliminar todos los contenedores:**
  ```sh
  docker rm $(docker ps -aq)
  ```

- **Acceder a un contenedor en ejecución:**
  ```sh
  docker exec -it <ID_CONTENEDOR> sh
  ```

- **Iniciar un contenedor detenido:**
  ```sh
  docker start <ID_CONTENEDOR>
  ```

- **Listar todos los contenedores (incluidos los detenidos):**
  ```sh
  docker ps -a
  ```

- **Ver imágenes disponibles en Docker:**
  ```sh
  docker images
  ```

- **Ejecutar un contenedor Apache con mapeo de puertos:**
  ```sh
  docker run -d -p 8080:80 --name mi_apache apache
  

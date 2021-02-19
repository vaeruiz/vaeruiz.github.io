---
layout: post
title:  "HTTPS y Let's Encrypt"
date:   2021-02-18 09:39:00 -0600
categories: Implantación de Aplicaciones Web
---
Instalando una aplicación web y añadiendo un certificado HTTPS.

## Preparando la máquina

Necesitamos una máquina con al menos 2GB de RAM y con los puertos HTTP(80), HTTPS(443) y MySQL(3306) abiertos.

## Preparando nuestro dominio

Ahora vamos a crear nuestro nombre de dominio, para ello tendremos que ir a la página [Freenom](https://www.freenom.com/es/index.html?lang=es), nos registramos en su página e iniciamos sesión, cuando estemos logueados vamos a Servicios>Registrar nuevo dominio. Se nos abrirá una nueva página en la que ingresaremos el nombre de dominio que queremos crear y pulsaremos el botón para comprobar la disponibilidad.

Si está libre, podremos elegir una lista de dominios, cuando seleccionemos el que queremos, en la parte superior saldrá que tenemos un doominio añadido junto con un botón llamado checkout, le damos y pasamos a la pantalla de "compra". Sobre el tiempo que estará el dominio disponible, seleccionamos 1 mes ya que esto es una prueba. 

Le damos a continuar, en la pantalla de confirmación aceptamos los términos y condiciones de uso, y le damos a completar encargo.

Cuando termine este proceso, volvemos a la ventana de servicios y vamos a Mis dominios, dentro veremos que ya podemos utilizar el dominio que hemos reservado antes, vamos a sus opciones (botón Manage Domain), una vez dentro vamos a la sección Manage Freenom DNS.

En la nueva página que se nos abre, deberemos de crear 2 registros DNS de tipo A que apunten a nuestra máquina de Amazon, en mi caso los registros han quedado de la siguiente manera.

![Imagen de demostracion 1](/capturas/captura1.png)

Guardamos los cambios que hemos hecho.

Después de esto el dominio empezará a procesarse por todos los lugares posibles del mundo, es cuestión de tiempo que esté en funcionamiento y podamos empezar a utilizarlo.

## Convirtiendo nuestro sitio en un sitio seguro

Después de este último paso instalamos nuestra aplicación web, y pasamos a convertir nuestro dominio http a https.

Para ello hacemos lo siguiente:

Vamos a la página de [Certbot](https://certbot.eff.org/instructions) (el enlace va directo al apartado de instrucciones), y seleccionamos nuestro tipo de servidor y SO, de forma automática nos llevará a los pasos que tenemos que hacer, en mi caso son los siguientes:

1. En la terminal, instalamos y actualizamos snapd

>sudo snap install core; sudo snap refresh core

2. Por si acaso, eliminanos cualquier instalación antigua que exista de certbot

>sudo apt-get remove certbot

3. Instalamos certbot con snapd

>sudo snap install --classic certbot

4. De forma adicional creamos un alias para poder utilizarlo

> sudo ln -s /snap/bin/certbot /usr/bin/certbot

5. Obtenemos el certificado

>sudo certbot --apache -m email@mail.es --agree-tos --no-eff-email -d nombre_dominio(ej. iaw-rcap.tk)

Si entramos en nuestro dominio, veremos que está reconocido como un sitio seguro y que dispone de un certificado SSL.

![Imagen de demostracion 1](/capturas/captura2.png)

![Imagen de demostracion 1](/capturas/captura3.png)

## Script de automatización del entorno

El script creado parte de la base de que se va a montar un Wordpress a través de la utilidad WPCLI.

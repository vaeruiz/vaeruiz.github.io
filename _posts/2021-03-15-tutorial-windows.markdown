---
layout: post
title:  "El clic derecho de Windows"
date:   2021-03-15 16:34:00 -0600
categories: Windows
---
Todos hemos "invocado" alguna vez el menú contextual de nuestro equipo, el famoso *clic derecho*, con él creamos carpetas, elegimos que hacer con nuestros archivos, ordenamos de forma automática el escritorio y muchas más cosas que nos permiten los sistemas Windows.

![Imagen-1](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img1.png?raw=true)

# Introducción

Pero... ¿Este menú se puede editar a nuestro gusto? Ya que imaginad el rendimiento que se le puede sacar añadiendo opciones personalizadas de, por ejemplo, los programas o scripts que más utilizamos y así poder tenerlo todo más a mano en vez de llenar nuestro escritorio de accesos directos.

# ¿Cómo se hace?

Aunque es algo complejo, es muy sencillo si prestamos atención adecuada y seguimos los pasos con cuidado, es muy recomendable tener conocimientos previos y básicos de informática.

# El editor de registro y los pasos necesarios

Primero debemos entrar al editor de registro de Windows llamado Regedit, podemos entrar de varias maneras:

1. **A través del símbolo del sistema.** Pulsando la tecla Windows de nuestro teclado o entrando al símbolo del sistema y en la barra de búsqueda ponemos "Regedit", se nos mostrará un programa llamado "Editor de registro".

2. **Por CMD.** En la consola de comandos escribimos regedit y lo ejecutamos.

3. **Ejecución directa.** La ejecución directa consiste en pulsar la combinación de teclas WIN+r para que se abra el menú de ejecución parecido a una consola de comandos más directa, al igual que en la opción de CMD, escribimos "regedit" y pulsamos enter.

Antes de desplegarse el programa se nos advertirá de que la aplicación puede hacer cambios en el sistema y nos preguntará si queremos ejecutarlo de todas formas, le damos a Sí y a continuación estaremos en nuestro editor de registro.

Encontraremos unos directorios que empiezan con el nombre de HKEY, el que nos interesa es HKEY_CLASSES_ROOT.

![Imagen-2](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img2.png?raw=true)

Este directorio regula, entre otras cosas, el comportamiento del menú en varios aspectos. A su vez contiene muchos otros directorios que como se ha dicho, sirven para otras cosas, los que nos permitirán añadir opciones al clic derecho del ratón son los directorios:

- **HKEY_CLASSES_ROOT\*\shell.** Se mostrarán las opciones al hacer clic derecho en cualquier tipo de archivo.

- **HKEY_CLASSES_ROOT\Directory\shell.** Se mostrarán las opciones configuradas al hacer clic derecho en cualquier directorio o carpeta.

- **HKEY_CLASSES_ROOT\DesktopBackground\Shell.** Las opciones añadidas se mostrarán al hacer clic derecho en cualquier parte del escritorio.

- **HKEY_CLASSES_ROOT\Directory\Background\shell.** En este caso, se verán las opciones del menú contextual al hacer clic derecho en cualquier directorio/carpeta y en el escritorio.

- **HKEY_CLASSES_ROOT\Drive\shell.** Las opciones del menú contextual que se mostrarán al hacer clic derecho sobre unidades de disco.

>Debido a que en HKEY_CLASSES_ROOT existen miles y miles de directorios, podemos escribir en la barra de búsqueda el directorio que nos interesa editar para localizarlo de una forma más rápida

Como se puede intuir cada HKEY_CLASSES_ROOT del que se ha hablado se puede utilizar para un ámbito de clic derecho distinto. Cada directorio tiene un \shell que está al final de cada tipo... ¡Tenemos que saber diferenciar las estructuras de directorios para no equivocarnos!

Cuando hayamos localizado qué menú contextual queremos cambiar, lo desplegamos, encontraremos una carpeta llamada "shell", hacemos clic derecho encima y le damos a Nuevo>Clave.

![Imagen-3](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img3.png?raw=true)

Se creará una nueva carpeta, le pondremos el nombre que queramos, en mi caso he llamado a esta carpeta Writer.

![Imagen-4](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img4.png?raw=true)

---
layout: post
title:  "Clic derecho de Windows"
date:   2021-03-15 16:34:00 -0600
categories: Windows
---
Todos hemos "invocado" alguna vez el menú contextual (a partir de ahora lo llamaré MC) de nuestro equipo, el famoso *clic derecho*, con él creamos carpetas, elegimos que hacer con nuestros archivos, ordenamos de forma automática el escritorio y muchas más cosas que nos permiten los sistemas Windows.

![Imagen-1](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img1.png?raw=true)

# Introducción

Pero... ¿Este menú se puede editar a nuestro gusto? Ya que imaginad el rendimiento que se le puede sacar añadiendo opciones personalizadas de, por ejemplo, los programas o scripts que más utilizamos y así poder tenerlo todo más a mano en vez de llenar nuestro escritorio de accesos directos.

# ¿Cómo se hace?

Aunque es algo complejo, es muy sencillo si prestamos la atención adecuada y seguimos los pasos con cuidado, es muy recomendable tener conocimientos previos y básicos de informática.

# El editor de registro y los pasos necesarios

Primero debemos entrar al editor de registro de Windows llamado Regedit, podemos entrar de varias maneras:

1. **A través del símbolo del sistema.** Pulsando la tecla Windows de nuestro teclado o entrando al símbolo del sistema, en la barra de búsqueda ponemos "Regedit", se nos mostrará un programa llamado "Editor de registro".

2. **Por CMD.** En la consola de comandos escribimos regedit y lo ejecutamos.

3. **Ejecución directa.** La ejecución directa consiste en pulsar la combinación de teclas WIN+r para que se abra el menú de ejecución parecido a una consola de comandos más directa, al igual que en la opción de CMD, escribimos "regedit" y pulsamos enter.

Antes de desplegarse el programa se nos advertirá de que la aplicación puede hacer cambios en el sistema y nos preguntará si queremos ejecutarlo de todas formas, le damos a Sí y a continuación estaremos en nuestro editor de registro.

Encontraremos unos directorios que empiezan con el nombre de HKEY, el que nos interesa es HKEY_CLASSES_ROOT.

![Imagen-2](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img2.png?raw=true)

Este directorio regula, entre otras cosas, el comportamiento del menú en varios aspectos. A su vez contiene muchos otros directorios que como se ha dicho, sirven para otras cosas, los que nos permitirán añadir opciones al clic derecho del ratón son los directorios:

- **HKEY_CLASSES_ROOT\*\shell.** Se mostrarán las opciones al hacer clic derecho encima de cualquier tipo de archivo.

- **HKEY_CLASSES_ROOT\Directory\shell.** Se mostrarán las opciones configurables al hacer clic derecho en cualquier directorio o carpeta.

- **HKEY_CLASSES_ROOT\DesktopBackground\Shell.** Las opciones añadidas se mostrarán al hacer clic derecho en cualquier parte del escritorio.

- **HKEY_CLASSES_ROOT\Directory\Background\shell.** En este caso, se verán las opciones del MC al hacer clic derecho en cualquier directorio/carpeta y en el escritorio.

- **HKEY_CLASSES_ROOT\Drive\shell.** Las opciones del MC que se mostrarán al hacer clic derecho sobre unidades de disco.

>Debido a que en HKEY_CLASSES_ROOT existen miles y miles de directorios, podemos escribir en la barra de búsqueda el directorio que nos interesa editar para localizarlo de una forma más rápida

Como se puede intuir cada HKEY_CLASSES_ROOT del que se ha hablado se puede utilizar para un ámbito de clic derecho distinto. Cada directorio tiene un \shell que está al final de cada tipo... ¡Tenemos que saber diferenciar las estructuras de directorios para no equivocarnos!

Cuando hayamos localizado qué MC queremos cambiar, lo desplegamos, encontraremos una carpeta llamada "shell", hacemos clic derecho encima y le damos a Nuevo>Clave.

![Imagen-3](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img3.png?raw=true)

Se creará una nueva "clave" a la que le tenemos que poner un nombre, en mi caso la he llamado Writer.

<a name="imagen4"></a>
![Imagen-4](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img4.png?raw=true)

Hecho esto hacemos clic derecho encima de nuestra nueva clave creada y hacemos lo mismo que antes, vamos a Nuevo>Clave, pero esta vez el nombre que le pondremos será "command", este paso siempre será necesario hacerlo para crear la clave de la opción que queremos añadir al MC.

![Imagen-5](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img5.png?raw=true)

Con esto hecho tendremos nuestra opción en el MC del ratón, sin embargo, ahora no hace nada porque no tiene ninguna acción asociada.

![Imagen-6](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img6.png?raw=true)

![Imagen-7](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img7.png?raw=true)


Para asociar una acción hacemos clic izquierdo una vez encima de la clave command que hemos creado, y a la derecha veremos un único valor que tiene el nombre de (Predeterminado), hacemos doble clic zquierdo sobre él para que se nos abra una nueva ventana en la que deberemos poner el comando o archivo que queremos que se ejecute al seleccionar la opción en el MC.

![Imagen-8](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img8.png?raw=true)

Después de darle a aceptar podemos comprobar que se ha añadido el comando de asociación a la acción del MC.

![Imagen-9](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img9.png?raw=true)

Ahora, si hacemos clic derecho en cualquier espacio de nuestro escritorio o en un directorio encontraremos la opción que hemos añadido y podremos comprobar que funciona.

![Gif-1](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/gif1.gif?raw=true)

# Extra, añade iconos a tu opción

Como se ha visto en la demostración, y si has decidido jugar un poco con el MC, la opción que hemos configurado sale pero, dependiendo de lo que queramos utilizar, se ve un poco soso si hemos añadido un programa como en este caso Writer.

Para añadirle un icono tenemos que ir a la raiz de la clave, que creamos al principio [imagen4](#imagen4), hacer clic izquierdo una vez sobre él y hacer clic derecho en el área en blanco que encontramos donde se encuentra el valor (Predeterminado), a continuación le damos a Nuevo>Valor de cadena y se nos creará un nuevo valor al que tendremos que llamarle Icon.

![Gif-2](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/gif2.gif?raw=true)

Ahora hacemos doble clic izquierdo encima del valor nuevo que hemos creado y en el cuadro "Información del valor" copiamos la ruta hasta donde se encuentra el icono que queremos que se muestre junto con la opción del MC.

![Imagen-10](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img10.png?raw=true)

Después de esto solo queda darle a Aceptar, y veremos nuestra opción personalizada con un icono.

![Imagen-11](https://github.com/vaeruiz/vaeruiz.github.io/blob/main/image/2021-03-15-post_tutorial-windows/img11.png?raw=true)


---

De esta forma podemos personalizar un poco nuestro sistema Windows y poder sacarle un poco más de partido teniendo programas o utilizades del día más a mano de lo que ya se puede tener.

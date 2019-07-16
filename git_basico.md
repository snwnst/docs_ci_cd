<a name="top"></a>

# Documentación básica de uso de Git

Este sección tratará sobre cómo empezar con **Git**. Partiremos explicando cómo configurarlo para empezar a trabajar con él. Al final de este capítulo deberías entender por qué existe Git, por qué usarlo, y tendrías que tener todo preparado para comenzar con los aspectos básicos. Para obtener información de los **Fundamentos de Git** y algunos conceptos relativos a las herramientas de control de versiones puedes dar click [aquí.](https://git-scm.com/book/es/v1/Empezando)

## Contenido:
 - [Instalación de Git](#instalacion)
 - [Configurando Git por primera vez](#create)
	 - [Configuración de usuario](#user)
 - [Inicializando un repositorio en un directorio existente](#init)
 - [Clonando un repositorio existente](#clone)
 - [Guardando cambios en el repositorio](#co) 
	 - [Comprobando el estado de tus archivos](#status)
	 - [Seguimiento de nuevos archivos/cambios](#add)
	 - [Confirmando tus cambios](#commit)
-  [Trabajando con repositorios remotos](#remote)
	- [Mostrando tus repositorios remotos](#remotev)
	- [Añadiendo repositorios remotos](#remoteadd)
	- [Recibiendo de tus repositorios remotos](#pull)
	- [Enviando a tus repositorios remotos](#push)
- [Creando etiquetas](#tag)
- [Ramificaciones en Git](#branch)
	- [Recibiendo rama de tus repositorios remotos](#track)

<a name="instalacion"></a>

## Instalación de Git
Para descargar la versión más reciente de Git desde su página web:
```
    https://git-scm.com/downloads
```
Cada versión de Git tiende a incluir útiles mejoras en la interfaz de usuario, por lo que utilizar la última versión es a menudo el camino más adecuado.

<a name="create"></a>

## Configurando Git por primera vez
Git trae una herramienta llamada `git config` que te permite obtener y establecer variables de configuración, que controlan el aspecto y funcionamiento de Git.

<a name="user"></a>

 - ### Configuración de usuario:
	Lo primero que deberías hacer cuando instalas Git es establecer tu nombre de usuario y dirección de correo electrónico. Esto es importante porque las confirmaciones de cambios (commits) en Git usan esta información, y es introducida de manera inmutable en los commits que envías:
	```
        $ git config --global user.name "<nombre cmpleto>"
        $ git config --global user.email <correo electronico>
	```
    Si quieres comprobar tu configuración, puedes usar el comando `git config --list` para listar todas las propiedades que Git ha configurado.

<a name="init"></a>

## Inicializando un repositorio en un directorio existente
Si estás empezando el seguimiento en Git de un proyecto existente, necesitas ir al directorio del proyecto y escribir:
```
    $ git init
```
Esto crea un nuevo subdirectorio llamado .git que contiene todos los archivos necesarios del repositorio —un esqueleto de un repositorio Git. Todavía no hay nada en tu proyecto que esté bajo seguimiento. 

<a name="clone"></a>

## Clonando un repositorio existente
Si deseas obtener una copia de un repositorio Git existente —por ejemplo, un proyecto en el que te gustaría contribuir— el comando que necesitas es  `git clone`.
Puedes clonar un repositorio con  `git clone [url]`. Por ejemplo, si quieres clonar este repositorio, harías algo así:
```
    $ git clone http://172.31.1.114:3000/DOCS/Documentacion.git
```
Git te permite usar distintos protocolos de transferencia. El ejemplo anterior usa el protocolo `http://`, pero también te puedes encontrar con `ssh://` o `<usuario>@<servidor>:<ruta.git>`, que utiliza el protocolo de transferencia SSH.

<a name="co"></a>

## Guardando cambios en el repositorio

<a name="status"></a>

 - ### Comprobando el estado de tus archivos:
	Tu principal herramienta para determinar qué archivos están en qué estado es el comando  `git status`. Si ejecutas este comando justo después de clonar un repositorio, deberías ver algo así:
	```
        $ git status
        # On branch master
        nothing to commit, working directory clean
	```
<a name="add"></a>

 - ### Seguimiento de nuevos archivos/cambios:
	 Para empezar el seguimiento de un nuevo archivo se usa el comando  `git add <nombre de archivo>`.  Por ejemplo, para iniciar el seguimiento del archivo README se ejecuta le comando de la siguiente manera:
	```
	    $ git add README
	```
	Para iniciar el seguimiento de todos los archivos a los cuales se haya habido modificaciones basta únicamente con ejecutar el de la siguiente manera:
	```
	    $ git add .
	```
<a name="commit"></a>

- ### Confirmando tus cambios:
	    La forma más fácil de confirmar es ejecutando  `git commit` ejemplo:
	```
	    $ git commit -m "<algun comentario acerca de los cambios>"
	```

<a name="remote"></a>

## Trabajando con repositorios remotos

Los repositorios remotos son versiones de tu proyecto que se encuentran alojados en algún punto de la red. Puedes tener varios, cada uno de los cuales puede ser de sólo lectura, o de lectura/escritura, según los permisos que tengas. Colaborar con otros implica gestionar estos repositorios remotos, y mandar (push) y recibir (pull) datos de ellos cuando necesites compartir cosas.

<a name="remotev"></a>

- ### Mostrando tus repositorios remotos:
	Para ver qué repositorios remotos tienes configurados, puedes ejecutar el comando  `git remote`. Mostrará una lista con los nombres de los remotos que hayas especificado. Si has clonado tu repositorio, deberías ver por lo menos "origin" —es el nombre predeterminado que le da Git al servidor del que clonaste—:

	```
	$ git remote
	origin
	```

	También puedes añadir la opción  `-v`, que muestra la URL asociada a cada repositorio remoto:
	```
	    $ git remote -v
	```

<a name="remoteadd"></a>

- ### Añadiendo repositorios remotos:
	Ya he mencionado y he dado ejemplos de repositorios remotos en secciones anteriores, pero a continuación veremos cómo añadirlos explícitamente. Para añadir un nuevo repositorio Git remoto, asignándole un nombre con el que referenciarlo fácilmente, ejecuta  `git remote add [nombre] [url]`:

	```
	    $ git remote add origin http://172.31.1.114:3000/DOCS/Documentacion.git
	```

<a name="pull"></a>

- ### Recibiendo de tus repositorios remotos:
	Para recuperar datos de tus repositorios remotos puedes ejecutar:

	```
	    $ git fetch [remote-name]
	```
	Este comando recupera todos los datos del proyecto remoto que no tengas todavía. Después de hacer esto, deberías tener referencias a todas las ramas del repositorio remoto, que puedes unir o inspeccionar en cualquier momento.
		
	Puedes usar el comando `git pull` para recuperar y unir automáticamente la rama remota con tu rama actual. Éste puede resultarte un flujo de trabajo más sencillo y más cómodo.
	```
	    $ git pull [remote-name]
	```

<a name="push"></a>

- ### Enviando a tus repositorios remotos:
	Cuando tu proyecto se encuentra en un estado que quieres compartir, tienes que enviarlo a un repositorio remoto. El comando que te permite hacer esto es sencillo:  `git push [nombre-remoto][nombre-rama]`. Si quieres enviar tu rama maestra (`master`) a tu servidor origen (`origin`), ejecutarías esto para enviar tu trabajo al servidor:
	```
	    $ git push origin master
	```
	Si de han creado etiquetas durante las confirmaciones y desea subir los cambios, Puedes usar el parámetro `-tags`.
	
	```
	    $ git push origin master -tags
	```

<a name="tag"></a>

## Creando etiquetas

Listar las etiquetas disponibles en Git es sencillo, Simplemente escribe  `git tag`:
```
    $ git tag
    v0.1
    v1.3
```
- ### Etiquetas anotadas:

	Crear una etiqueta anotada en Git es simple. La forma más fácil es especificar  `-a`  al ejecutar el comando  `tag`:

	```
        $ git tag -a v1.4 -m 'descripción de mi versión 1.4'
        $ git tag
        v0.1
        v1.3
        v1.4
	```

	El parámetro  `-m`  especifica el mensaje, el cual se almacena con la etiqueta. Si no se especifica un mensaje para la etiqueta anotada, Git lanza tu editor para poder escribirlo.

<a name="branch"></a>

## Ramificaciones en Git

<a name="track"></a>

- ### Recibiendo rama de tus repositorios remotos:
	Necesitas crear una rama local que rastree una rama remota. El siguiente comando creará una rama local llamada **desarrollo** , rastreando el **origin** rama remota **/ desarrollo** . Cuando presione sus cambios, la rama remota se actualizará.
	```
		git checkout --track origin/desarrollo
	```

    [Subir](#top)
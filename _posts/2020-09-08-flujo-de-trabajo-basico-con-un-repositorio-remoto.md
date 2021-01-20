---
layout: post
title: Flujo de trabajo básico en Git con un repositorio remoto
subtitle: Introducción a servidores remotos como GitHub
gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
tags: [Git]
comments: true
---
Este post es introductorio a lo que será GitHub, retomaré conceptos que deben quedar claros para este momento. También repasaremos lo que son las ramas en los repositorios remotos.

### ¿Qué es GitHub?

Gracias a Git todas las actualizaciones y correcciones que hagamos a nuestro proyecto o código quedarán almacenados en nuestra computadora, esto significa que no hay forma de que otras personas que formen parte de nuestro equipo puedan ver nuestros cambios, o qué, si por algun motivo tu disco duro se formatea no volverás a ver tu código :(. Para solucionar esto existen los servidores remotos :clap: como GitHub (el favorito), pero también está GitLab o BitBucket.

Lo que hacen estos sitios es guardar el mismo repositorio que tu tienes en tu ordenador y darnos un URL para acceder a los archivos del proyecto y poder descargarlos, hacer cambios, comparar versiones, almacenarlos, etc.

### Conceptos que deben de quedar claro antes de pasar nuestro repositorio a un repositorio remoto

Directorio de trabajo → entorno de desarrollo personal, la carpeta en donde están mis archivos.

Cuando pones el concepto `git init`, aparecen dos conceptos nuevos:

1. Preparación o staging  que es lugar al que enviamos los archivos antes de mandarla a la base de datos historicos que se han hecho al proyecto que es el repositorio local

2. Cuando quieres agregar un archivo de tu directorio de trabajo a preparación o staging ponemos. Esto le permite a git hacer un tracking, un rastreo de los cambios que ocurren en ese archivo. [Este es un lugar temporal, que si no haces algo con el, eventualmente va a desaparecer]

El siguiente flujo de trabajo es el que existe en tu computadora cada que agregas cambios a tu código y lo actualizas con Git.

![Imagen](https://luisaalfaro.github.io/lovelace-blog/assets/img/Stating.jpg)

Para no repetir los comandos en este post y evitar hacerlo largo y tedioso, te recomiendo que revises el post "Primeros apuntes sobre Git" y "Funcionamiento de Git".

### ¿Qué necesito para envíar mi repositorio en Git a GitHub?

Una cuenta en GitHub. Es sumanente sencillo, solo entra a la pagina de GitHub y crea tu cuenta.

### Nuevos comandos para aprender

Para obtener un repositorio de un remoto: 
`git clone (URL)`
Se trae una copia de *master* a tu carpeta.

Para mandar de un repositorio local a un repositorio remoto usamos el comando
`git push`

Para traer del repositorio remoto al repositorio local, pero no lo copia en mis archivos
`git fetch`

Para que lo copie con mis archivos y fusionar debo de agregar el comando
`git merge`

el que fusiona los últimos dos comandos se llama
`git pull`

### Ramas o branches de Git

Master es nuestra rama principal, ahí tenemos todos los commits.

Head es el commit más reciente.

Las ramas son la forma de hacer cambios en nuestro proyecto sin afectar el flujo de trabajo de la rama principal. Esto porque queremos trabajar una parte muy específica de la aplicación o simplemente experimentar.

La cabecera o `HEAD` representan la rama y el commit de esa rama donde estamos trabajando. Por defecto, esta cabecera aparecerá en el último commit de nuestra rama principal. Pero podemos cambiarlo al crear una rama (`git branch rama`, `git checkout -b rama`) o movernos en el tiempo a cualquier otro commit de cualquier otra rama con los comandos (`git reset id-commit`, `git checkout rama-o-id-commit`).

### Marge

El comando git merge nos permite crear un nuevo commit con la combinación de dos ramas (la rama donde nos encontramos cuando ejecutamos el comando y la rama que indiquemos después del comando).

```sh
#Crear un nuevo commit en la rama master combiando 
#los cambios de la rama cabecera:
git checkout master
git marge cabecera

#Crear un nuevo commit en la rama cabecera combinando
#los cambios de cualquier otra rama:
git checkout cabecera
git marge cualquier-otra-rama
```

Importante: guardar cambios antes de hacer checkout.

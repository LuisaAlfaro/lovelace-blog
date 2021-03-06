---
layout: post
title: Merge y Pull Requests de ramas de desarrollo a master
subtitle: Diferencia entre un Merge y un Pull Requestst. Aprendiendo a trabajar en un flujo de trabajo profesional con Git y GitHub
gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
tags: [Git]
comments: true
---

No olvidar que Git es un software de control de versiones pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de un código en tu computadora, es un repositorio local. Por otro lado, GitHub es una forja para alojar proyectos utilizando el sistema de control de versiones Git, es un repositorio remoto. 

Este control de versiones se vuelve poderoso cuando trabajamos en un equipo grande o cuando nuestro proyecto requiere muchos cambios y versiones. 
Por defecto, cualquier persona puede clonar o descargar tu proyecto desde GitHub, pero no pueden crear commits, ni ramas, ni nada.

Existen varias formas de solucionar esto para poder aceptar contribuciones. Una de ellas es añadir a cada persona de nuestro equipo como colaborador de nuestro repositorio.

Solo debemos entrar a la configuración de colaboradores de nuestro proyecto (`Repositorio > Settings > Collaborators`) y añadir el email o username de los nuevos colaboradores. Para sacar el máximo potencial de Git y GitHub los Merges y Pull Requests son fundamentales de comprender. 

En este post voy a explicar qué significa cada uno, sus diferencias y por supuesto, los comandos y flujo de trabajo para cada uno.

### Flujo de trabajo profesional con merge en Git de ramas de desarrollador a master

Todos los repositorios de git, tienen la rama master (este sería el repositorio en producción) Cuando queremos hacer una modificación de un archivo en un repositorio que está en producción, crearemos una rama alternativa con la que podremos trabajar y así no alterar el funcionamiento del repositorio master.

Básicamente el flujo de trabajo es:

1. Crear ramas:
`git branch <nombre de la rama>`

2. El programador baja el repositorio con: 
`git pull origin master`

3. Asignar una rama a cada persona que programa para cambiar de rama utilizamos:
`git checkout <nombre de la rama>`

Comienzas a trabajar en esa rama y hacer los commits necesarios

Quien programo desde esa rama sube su trabajo con:
`git push origin <nombre de la rama>`

Quien coordina baja y unifica todos los cambios con los siguientes coomandos:
`git checkout <nombre de la rama>`

Ya que estamos en la rama que vamos a unificar,  escribimos:
`git pull origin <nombre de la rama>`

`git push origin <nombre de la rama>`


Una vez que tengo la rama actualizada, procedo a hacer el merge con master
`git checkout master`
`git merge <nombre de la rama>`

Finalmente envío la rama master actualizada a Github 😃
`git pull origin master`
`git push origin master`

### Flujo de trabajo profesional con Pull Requests en GitHub

En un entorno profesional normalmente se bloquea la rama master, y para enviar código a dicha rama pasa por un *code review* y luego de su aprobación se unen códigos con los llamados Pull Requests. Esta es una función de GitHub, no de Git.

Para realizar pruebas enviamos el código a servidores que normalmente a un servidor de prueba, luego de que se realizan las pruebas pertinentes tanto de código como de la aplicación estos pasan al servidor de producción con el ya antes mencionado merge request.

*Utilizando Pull Requests en GitHub*

Es una función en la que una persona colaboradora del proyecto pide que revisen sus cambios antes de hacer merge a una rama, normalmente master.

Al hacer un Pull Request se genera una conversación que pueden seguir las demás usuarias del repositorio, así como autorizar y rechazar los cambios.

El flujo del pull request es el siguiente

1. Se trabaja en una **rama paralela** los cambios que se desean 
`git checkout <nombre de la rama>`

2. Se trabaja el código y se hacen los **commit necesarios** a la rama 
`git add .`
`git commit -m "comentario"`

			o 

`git commit -am "comentario"`

3. Se suben al **remoto** los **cambios** (GitHub)
`git push origin <nombre de la rama>`

En la terminal es todo lo que se hace y después nos vamos a GitHub y hacemos el 

`pull request` 

4. Comparando la **rama master** con la rama en la que se hicieron los cambios.

-Uno, o varios colaboradores revisan que el **código sea correcto** y dan **feedback** (en el chat del pull request)

-El colaborador hace los cambios que desea en la **rama** y lo **vuelve a subir** al remoto 

-Se **aceptan los cambios** en GitHub

-Se hace **merge** a `master` desde GitHub

**Importante**: Cuando se modifica una `rama`, también se modifica el `pull request`.

Los pull requests en Git no existen, solo existe los merges. Es como trabajar en un stagin que te permite agregar cambios.
---
layout: post
title: Funcionamiento de Git.
subtitle: Flujos de trabajo en Git y las ramas.
gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
tags: [Git]
comments: true
---

En este post explicaré el ciclo básico de trabajo en Git y los comandos más utilizados para el mismo. También hablaré sobre las ramas y para qué sirven.
Aprovecho para aclarar que Git no es lo mismo que GitHub. Primero necesitamos tener claro el flujo de trabajo en Git antes de pasarnos a los repositorios remotos (GitHub)

### Explicación de los comandos de Git para después explicar los ciclos de estado de un archivo en Git ###

Para iniciar un repositorio en tu computadora, o sea, activar el sistema de control de versiones de Git en tu proyecto (código), solo debes ejecutarl el comando `git init` en la terminar.

Este comando se encargará de dos cosas: 

1. Crear una carpeta `.git`, donde se guardará toda la base de datos con cambios atómicos de nuestro proyecto.
2. Crear un área que conocemos como **Staging**, que guardará temporalmente nuestros archivos (cuando ejecutemos un comando especial para eso) y nos permitirá, más adelante, guardar estos cambios en el repositorio (también con un comando especial).

Ya activado el control de versiones los siguientes comandos son los que utilizaremos:

- **`git status`**: nos permite ver el estado de todos nuestros archivos y carpetas.

- **`git add`**: nos ayuda a mover archivos del Untracked o Unstaged al estado Staged. Podemos usar `git nombre-del-archivo-o-carpeta` para añadir archivos y carpetas individuales o `git add -A` para mover todos los archivos de nuestro proyecto (tanto Untrackeds como unstageds).

- **`git reset HEAD`**: nos ayuda a sacar archivos del estado Staged para devolverlos a su estado anterior. Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked.

- **`git commit`**: nos ayuda a mover archivos de Unstaged a Staged. Esta es una ocasión especial, los archivos han sido guardado o actualizados en el repositorio. Git nos pedirá que dejemos un mensaje para recordar los cambios que hicimos y podemos usar el argumento `m` para escribirlo (`git commit -m "mensaje"`).

- **`git rm`**: este comando necesita alguno de los siguientes argumentos para poder ejecutarse correctamente:`git rm --cached`: Mueve los archivos que le indiquemos al estado Untracked.`git rm --force`: Elimina los archivos de Git y del disco duro. Git guarda el registro de la existencia de los archivos, por lo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

### Ciclos de vida o estados de los archivos en Git ###

**Ciclo de vida o estados de los archivos en Git**:Cuando trabajamos con Git nuestros archivos pueden vivir y moverse entre 4 diferentes estados:

1. **Archivos Tracked**: son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos `git add` y `git commit`.

2. **Archivos Staged**: son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando `git add`, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios, pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando `git commit`.

3. **Archivos Unstaged**: entiéndelos como archivos *“Tracked pero Unstaged”*. Son archivos que viven dentro de Git pero no han sido afectados por el comando `git add` ni mucho menos por `git commit`. Git tiene un registro de estos archivos, pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.

4. **Archivos Untracked**: son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por `git add`, así que Git no tiene registros de su existencia.Recuerda que hay un caso muy raro donde los archivos tienen dos estados al mismo tiempo: staged y untracked. Esto pasa cuando guardas los cambios de un archivo en el área de Staging (con el comando `git add`), pero antes de hacer commit para guardar los cambios en el repositorio haces nuevos cambios que todavía no han sido guardados en el área de Staging (en realidad, todo sigue funcionando igual pero es un poco divertido).

La siguiente figura es un resúmen gráfico de lo que les expliqué con anterioridad.

![Imagen](/Users/luisaalfaro/lovelace-blog/_posts/imagenes post/Staging.jpg)

### ¿Qué es una rama y cómo funciona un marge en Git ###

Sin dudas el verdadero potencial de hacer de Git tu mejor amigo es la creación de branch o ramas (en español). Una rama es como un universo alterno de tu código original que es almacenado en master.

Todos los commits se aplican sobre una rama. Por defecto, siempre empezamos en la rama master y creamos nuevas ramas, a partir de esta, para crear flujos de trabajo independientes.

Crear una nueva rama se trata de copiar un commit (de cualquier rama), pasarlo a otro lado (a otra rama) y continuar el trabajo de una parte específica de nuestro proyecto sin afectar el flujo de trabajo principal (que continúa en la rama master o la rama principal).

Esto hace que equipos de desarrollo con un número considerable de personas puedan trabajar en el mismo código sin afectar el trabajo de los demás. ¡Qué sueño!

Para cear una nueva rama utilizamos el comando: `Checkout`. 

Y para unir dos ramas hacemos un `Merge`.

Podemos crear todas las ramas y commits que queramos. De hecho, podemos aprovechar el registro de cambios de Git para crear ramas, traer versiones viejas del código, arreglarlas y combinarlas de nuevo para mejorar el proyecto.

Solo ten en cuenta que combinar estas ramas (sí, hacer “merge”) puede generar conflictos ya que algunos archivos pueden ser diferentes en ambas ramas. 
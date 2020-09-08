---
layout: post
title: Primeros apuntes sobre Git
subtitle: ¿Qué es git? ¿Para qué sirve? Comandos básicos
gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
#tags: [test]
comments: true
---
En este post resolveré las primeras dudas sobre Git y GitHub y por qué es una herramienta maravillosa para las personas que trbajamos con código. También proporcionaré los comandos básicos de la terminar y de git para comenzar a usar este poderoso sowftware de control. Esa lista te será útil por siempre :).

Git es un software de control de versiones diseñado por **Linus Torvalds**, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de un código. Y GitHub es una forja para alojar proyectos utilizando el sistema de control de versiones Git. GitHub es La Red Social de código para programadoras incluso tu propio curriculum vitae. 

El control de versiones es una de las tareas fundamentales para la administración de un proyecto de desarrollo de software o de un proyecto de código como un análisis estádistico en Rstudio. Surge de la necesidad de mantener y llevar control del código que vamos programando, para no tener en nuestra computadora 4 archivos sobre lo mismo, pero con versiones diferentes. Es absolutamente necesario para conservar el orden en proyectos y aún más para trabajo en equipo. 

Al principio puede parecer retador, pero verás que es más sencillo de lo que puedes sospechar.

### ¿Por qué usar un control de versiones como Git? ###
Porque nos ayuda a guardar el historial de cambios y crecimiento de los archivos de nuestro proyecto. Git te permite guardar de forma optima los cambios por mínimos que sean. Olvidate de:

- Código.csv
- Coodigo.csv
- Ahorasícodigo.csv
- Estesieselbueno.csv

Utilizar Git te permitirá guardar todos estos cambios de forma incremental, o sea aplicando cambios sobre los últimos cambios y te da la oportunidad de regresar a tu primer versión en el momento que tu quieras.

### ¿Qué necesitas para poder comenzar a controlar tus codigos con control de versiones? ###

Si utilizas windows necesitas instalar Git Bash y debes elegir si prefieres trabajar con la forma de Windows o la forma de UNIX (Linux y Mac).

Linux y Mac tienen su terminal de facto.

También es necesario instalar un editores de código. Un editor de código es una herramienta que nos brinda ayuda para escribir código, algo así como un bloc de notas muy avanzado. Los editores más populares son VSCode, Sublime Text y Atom. Elige el que prefieras. Hay cientos de ellos.

Ya instalado, podemos comenzar con la Introducción a a la terminal y línea de comandos.

### Te comparto los comandos básicos de la terminal y que serán tus mejores amigos ###

´pwd: Nos muestra la ruta de carpetas en la que te encuentras ahora mismo.

'mkdir': Nos permite crear carpetas (por ejemplo, mkdir Carpeta-Importante).

'touch': Nos permite crear archivos (por ejemplo, touch archivo.txt).

'rm': Nos permite borrar un archivo o carpeta (por ejemplo, rm archivo.txt). Mucho cuidado con este comando, puedes borrar todo tu disco duro.

'cat': Ver el contenido de un archivo (por ejemplo, cat nombre-archivo.txt).

'ls': Nos permite cambiar ver los archivos de la carpeta donde estamos ahora mismo. Podemos usar uno o más argumentos para ver más información sobre estos archivos (los argumentos pueden ser -- + el nombre del argumento o - + una sola letra o shortcut por cada argumento).

'ls -a': Mostrar todos los archivos, incluso los ocultos.

'ls -l': Ver todos los archivos como una lista.

'cd': Nos permite navegar entre carpetas.

'cd /': Ir a la ruta principal:

'cd o cd ~': Ir a la ruta de tu usuario

'cd carpeta/subcarpeta': Navegar a una ruta dentro de la carpeta donde estamos ahora mismo.

'cd .. (cd + dos puntos)': Regresar una carpeta hacia atrás.

Si quieres referirte al directorio en el que te encuentras ahora mismo puedes usar 'cd .' (cd + un punto)

'history': Ver los últimos comandos que ejecutamos y un número especial con el que podemos repetir su ejecución.

'! + número': Ejecutar algún comando con el número que nos muestra el comando history (por ejemplo, !72).

' clear ': Para limpiar la terminal. También podemos usar los atajos de teclado Ctrl + L o Command + L.

### Y por último te comparto los comandos básicos de Git ###

El comando para iniciar nuestro repositorio, o sea, indicarle a Git que queremos usar su sistema de control de versiones en nuestro proyecto, es 'git init'

El comando para que nuestro repositorio sepa de la existencia de un archivo o sus últimos cambios es 'git add'
Este comando no almacena las actualizaciones de forma definitiva, solo las guarda en algo que conocemos como “Staging Area” (Lo explicaré más adelante).

El comando para almacenar definitivamente todos los cambios que por ahora viven en el staging area es 'git commit'
También podemos guardar un mensaje para recordar muy bien qué cambios hicimos en este commit con el argumento '-m "Mensaje del commit".'

Por último, si queremos mandar nuestros commits a un servidor remoto, un lugar donde todos podamos conectar nuestros proyectos, usamos el comando 'git push'.

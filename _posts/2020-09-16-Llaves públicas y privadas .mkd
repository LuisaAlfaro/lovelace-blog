---
layout: post
title: Llaves públicas y privadas en Git y vincularlas con GitHub
subtitle: Crear una clave SSH en Git y vincularla con GitHub.
gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
tags: [Git]
comments: true
---

La criptografía asimétrica es el método que asegura que un mensaje enviado no puede ser leído por ninguna persona que no sea la destinataria del mensaje. Para que exista una criptografía asimétrica en Git y GitHub existen las llaves públicas y privadas.
Cada persona y cada computadora pueden tener una y es única.

Las llaves públicas y privadas nos ayudan a cifrar y descifrar archivos de forma que no existe el riesgo de que sean interceptados por personas con malas intenciones.

Las llaves o claves SSH (una pública y una privada), nos permiten conectarnos fácilmente a un servidor o a múltiples servidores, sin tener que ingresar una contraseña, en otras palabras son una manera de identificar nuestras computadoras de confianza.

### ¿Cómo funciona el cifrado asimétrico?

Supongamos que Luisa quiere enviarle un mensaje a Montse, pero es un mensaje confidencial que sólo ellas dos pueden leer.

Primero para que Luisa le envíe un mensaje a Montse, Luisa cifra el mensaje con la llave pública de Montse y luego firma con su propia llave privada. 

Si alguien captura el mensaje no podrá leerlo porque no tiene la llave privada de Montse.

Montse confirma que el mensaje es de Luisa usando la llave pública de Luisa y luego cifra el mensaje con su propia llave privada.

#### Importante:
Luisa y Montse deben generar una llave pública y privada.
Luisa y Montse deben de intercambiar sus llaves públicas.
Luisa y Montse deben cifrar el mensaje con la llave pública recibida.
Luisa y Montse podrán leer el mensaje con la llave privada que generaron.

### Crear nuestras llaves para compartir archivos con GitHub sin correr el riesgo de que sean interceptados.

#### Configura tus llaves SSH en local.

Explicaré el proceso para crear una llave SSH en local y usarlas al hacer login en servidores remotos, de modo que podamos aumentar la seguridad de las conexiones (Para Window, Linux y Mac). ¿Listas?

1. En tu terminal, generar tus llaves SSH, revisa que estés en Home. Recuerda que es muy buena idea proteger tu llave privada con una contraseña.

`ssh-keygen -t rsa -b 4096 -C "tu@email.com"`

2. Configurar nuestro sistema.

##### En Windows y Linux:

Encender el "servidor" de llaves SSH de tu computadora, agrega el siguiente comando a tu termial:

`eval $(ssh-agent -s)`

Añadir tu llave SSH a este "servidor":

`ssh-add ruta-donde-guardaste-tu-llave-privada`

##### En Mac:

Encender el "servidor" de llaves SSH de tu computadora:

`eval "$(ssh-agent -s)"`

Si usas una versión de OSX superior a Mac Sierra (v10.12) debes crear o modificar un archivo "config" en la carpeta de tu usuario con el siguiente contenido (ten cuidado con las mayúsculas):

`Host *`
        `AddKeysToAgent yes`
        `UseKeychain yes`
        `IdentityFile ruta-donde-guardaste-tu-llave-privada`

Añadir tu llave SSH al "servidor" de llaves SSH de tu computadora (en caso de error puedes ejecutar este mismo comando pero sin el argumento -K):
 `ssh-add -K ruta-donde-guardaste-tu-llave-privada`

¿Cómo verificar si ya existen llaves SSH?
Ejecuta el siguiente comando en Git local:
`ls -al ~/.ssh`

### Conexión a GitHub con SSH

1. Vamos a nuestra cuenta de github, y en donde esta nuestro avatar damos clic → settings.

2. Dar clic en SSH and GPG keys

3. Clic New SSH key or Add SSH key.
Te aparecerán los siguientes input:

- SSH Keys
- Title
- Key

En donde Title, puede ser un título descriptivo, por ejemplo "Mi PC"

Y en Key vas a pegar lo que aparece cuando ejecutes el siguiente comando en la terminal con git local:

 `cat ~/.ssh/id_rsa.pub`

Todo lo que te apareció, lo debes pegar en la area que dice Key, después dar click en *"Add SSH key".*
Por seguridad tendrás que hacer login, y si vuelves a dar clic en *New SSH key* or *Add SSH key*, notaras que ya aparece tu clave SSH.

Ahora podemos actualizar la URL que guardamos en nuestro repositorio remoto, solo que, en vez de guardar la URL con HTTPS, vamos a usar la URL con SSH:

 `git remote set-url origin url-ssh-del-repositorio-en-github`
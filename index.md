# Práctica 1 - Configuración de máquina virtual en el IaaS
* * *

* Nombre: Héctor Rodríguez Alonso.
* Fecha: 2022-02-20.
* Correo: alu0101365107@ull.edu.es.

* * *
# Indice
* [Resumen](#resumen)
* [Objetivos](#objetivos)
    * [Configuración previa](#configuracion-previa)
    * [Instalación de git y node.js](#instalaci%C3%B3n-de-git-y-nodejs)
* [Conlusiones](#conclusiones) 

## Resumen

## Objetivos 

### Configuración previa
1. __Encendido y visualización de la IP de la VPS__
    * Deberemos de acceder al [IAAS](https://iaas.ull.es/ovirt-engine/sso/login.html) y tomar nuestra máquina, encenderla y esperar a que esté operativa.
    * Una vez la VPS este ejecutándose correctamente, accedemos a ella mediante la consola VNC en explorador y nos validaremos, una vez hecho esta pedirá que cambiemos la contraseña. 
    * Al finalizar los pasos anteriores, nos tendremos que volver a validar y deberemos de ejecutar el siguiente comando: `ifconfig -a`.
    ![](./images/Captura.PNG)
2. __Configuración del SSH en VSCODE__
    * Crearemos una nueva conexión con Remote-SSH ejecutando `ssh usuario@10.6.130.7`
    * Editaremos el fichero config de Remote-SSH y añadiremos `Host DSI`, para así no tener que acordarnos de la IP siempre. Quedaría de la siguiente forma:  
    ```
        Host DSI
            HostName 10.6.130.7
            User usuario
    ```
    * Comprobaremos que poseemos la siguiente opción a la hora de hacer al connect del Remote-SSH de la VPS.
    ![](./images/Captura14.PNG)
    > **De esta forma solo tendremos que poner la contraseña cada vez que accedamos o tengamos que cambiar de directorio en el menú propio de VSCODE.**
    >
3. __Configuración básica de la VPS__
    * Visualizaremos el hostname de la VPS mediante `cat /etc/hostname` y modificaremos _ubuntu_ por _iaas-dsi_ con `sudo vi /etc/hostname`, una vez hecho, verificamos el cambio con el primer comando usado.
    ![](./images/Captura2.PNG)
    * Mmediante `cat /etc/hosts` observaremos el fichero hosts y modificaremos _ubuntu_ por _iaas-dsi_ con `sudo vi /etc/hosts`, verificamos el cambio con el primer comando usado. 
    ![](./images/Captura3.PNG)
    * Lanzaremos los siguientes comandos `sudo apt update` y `sudo apt upgrade` para actualizar nuestra VPS, una vez finalicen, reiniciamos la máquina.
    ![](./images/Captura4.PNG)
    * Mediante el comando `ssh-keygen` obtendremos una RSA, la cual utilizaremos más adelante.
    ![](./images/Captura5.PNG)

## Instalación de Git y Node.js
1. __Github__
    * Mediante el comando `sudo apt install git` instalaremos el paquete de Git.
    * Una vez instalado el paquete, deberemos de configurar el usuario y correo de nuestra cuenta de GitHub al paquete. Para ello usaremos `git config --global user.name " "`donde colocaremos nuestro nombre y `git config --global user.mail " " ` colocando el correo. Usaremos la flag _--global_ para no tener que estar configurando este en cada repositorio que creemos.
    ![](./images/Captura6.PNG)
    * Accederemos a [GitHub](https://github.com/), nos validaremos, entraremos a ajustes, SSH y GPG, ahí añadiremos una nueva Key, la cual es la RSA generada anteriormente.
    ![](./images/Captura8.PNG)
2. __Cambio en el estilo de la terminal__
    * A la hora de cambiar el estilo en la terminal, deberemos de descargar el script [git prompt](https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh). Una vez descargado, lo colocaremos en nuestra VPS al mismo nivel que  el fichero _.bashrc_, en este añadiremos la siguiente línea;  
    ```
    PS1='\[\033]0;\u@\h:\w\007\]\[\033[0;34m\][\[\033[0;31m\]\w\[\033[0;32m\]($(git branch 2>/dev/null | sed -n "s/\* \(.*\)/\1/p"))\[\033[0;34m\]]$'
    ```
    ![](./images/Captura7.PNG)

3. __Comprobación de la terminal y vinculación de GitHub__
    * Si hemos realizado los pasos anteriormente mencionados, podremos clonar un repositorio nuestro directamente de github sin problemas y en nuestra terminal, entre paréntesis, observaremos la rama actual.
    ![](./images/Captura9.PNG)
    ![](./images/Captura10.PNG)

4. __Node.js__
    * Para instalar el gestor de versiones de Node.js (nvm), usaremos el comando `wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash`, reiniciaremos bash con `exec bash -l` y comprobaremos la version de este `nvm --version`.
    ![](./images/Captura11.PNG)
    * Mediante `nvm install node`, obtendremos la version más reciente de Node, además de la instalación del gesto de paquetes (npm), comprobaremos este con `nvm --version` y `npm --version`.
    ![](./images/Captura12.PNG)
    * Por último podremos visualizar las posibles versiones de Node con `nvm list`, en caso de no tener una versión instalada, usaremos `nvm install _version_`. Para cambiar de versión lo haremos con `nvm use _version_` y comprobaremos el cambio con `nvm --version` y `npm --version`, ya que el gesto de paquetes también ha podido cambiar de versión.
    ![](./images/Captura13.PNG)

### Conclusiones
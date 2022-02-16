# Práctica 1 - Configuración de máquina virtual en el IaaS
* * *
**Desarrollo en Sistemas Informáticos**

* Nombre: Héctor Rodríguez Alonso.
* Fecha: 2022-02-20.
* Correo: alu0101365107@ull.edu.es.

* * *
# Indice
* [Configuración](#configuracion-previa)
* [Instalación](#Instalación-de-git-y-Node.js)

## Configuracion previa
<img src="./images/Captura.PNG" width="50" height="100">
1. Encendido y visualización de la IP de la VPS
    * Deberemos de acceder al [IAAS](https://iaas.ull.es/ovirt-engine/sso/login.html) y tomar nuestra máquina, encenderla y esperar a que esté operativa.
    * Una vez la VPS este ejecutándose correctamente, accedemos a ella mediante la consola VNC en explorador y nos validaremos, una pasado hecho esta pedirá que cambiemos la contraseña. 
    * Al finalizar los pasos anteriores, nos tendremos que volver a validar y deberemos de ejecutar el siguiente comando: ```ifconfig -a```.
    ![](./images/Captura.PNG)
2. Configuración del SSH en VSCODE
    * Crearemos una nueva conexión con Remote-SSH ejecutando ```ssh usuario@10.6.130.7```
    * Editaremos el fichero config de Remote-SSH y añadiremos ```Host DSI```, para así no tener que acordarnos de la IP siempre. Quedaría de la siguiente forma:
    ```Host DSI\n
        HostName 10.6.130.7\n
        User usuario\n
    ```


## Instalación de git y Node.js

![](./images/Captura2.PNG)
![](./images/Captura3.PNG)
![](./images/Captura4.PNG)
![](./images/Captura5.PNG)
![](./images/Captura6.PNG)
![](./images/Captura7.PNG)
![](./images/Captura8.PNG)
![](./images/Captura9.PNG)
![](./images/Captura10.PNG)
![](./images/Captura11.PNG)
![](./images/Captura12.PNG)
![](./images/Captura13.PNG)


Cambio en el hostname
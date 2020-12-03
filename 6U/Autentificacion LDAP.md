# Cliente con autentificación LDAP.

![](./png/logo.png)

                                    Gontran Pestana Fernandez


#1.Preparativos

-Necesitamos unna MV con un servidor DS-389 instalado con varios usuarios.

-Y una segunda MV con OpenSuse.

Comprobamos el acceso LDAP desde el ciente:


![](./png/1.png)



![](./png/2.png)



#2.Configuracion de la autentificación LDAP.

##Conexión con el servidor.

-Ir a Yast -> LDAP y Kerberos.

-Y lo configuramos como la imagen siguiente para tener acceso al servidor.

![](./png/3.png)

![](./png/4.png)


##Comprobamos la estancia por comandos.

-En la consola del cliente con el usuario root:


![](./png/2.2.png)


![](./png/2.2.2.png)



#3.Crear usuarios y grupos dentro de LDAP desde el cliente.

-Iremos a Yast -> Gestión de usuarios y grupos.

-Seleccionaremos el filtro de LDAP users.

-Indentificarse en Bind DN


![](./png/5.png)


##En este apartado el servidor LDAP deja de autentificar al cliente.

![](./png/5.1.png)

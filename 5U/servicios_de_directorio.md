# Servicio de Directorio con comandos.

![](./png/logo.png)

Gontran Pestana   Fernández     2ºASIR - P4



# 1. Nombre de equipo FQDN.

- Vamos a usar una MV OpenSUSE para montar nuestro servidor LDAP.

- Revisar /etc/hostname. Debe tener un FQDN=serverXXg.curso2021.

- Revisar /etc/hosts

![](./png/1.1.png)


# 2. Instalar el Servidor LDAP.

  # Instalación del paquete.

- zypper in 389-ds, instalar el script de instalación.

- rpm -qa | grep 389-ds, comprobar la versión.

![](./png/2.1.png)


# Configurar la instancia.

- Crear el fichero /root/instance.inf con el siguiente contenido.

![](./png/2.2.1.png)


- dscreate from-file /root/instance.inf, creamos una nueva instancia.


- dsctl localhost status, comprobar el estado actual de la instancia de la base de datos LDAP.

![](./png/2.2.2.png)


- Creamos el fichero /root/.dsrc con el siguiente contenido.

![](./png/2.3.1.png)



# Comprobamos el servicio

![](./png/2.3comprobacion.png)



# Comprobar el aceso al contenido del LDAP.

- ldapsearch -b "dc=ldap09,dc=curso2021" -x | grep dn, muestra el contenido de nuestra base de datos LDAP.

![](./png/2.4.1.png)


- ldapsearch -H ldap://localhost -b "dc=ldapXX,dc=curso2021" -W -D "cn=Directory Manager" | grep dn, usando usuario/clave.

![](./png/2.4.2.png)


# 3. Añadir usuarios LDAP por comandos.

# Buscar Unidades Organizativas

Deberían estar creadas las OU People y Groups.

![](./png/3.1.png)


# Agregar usuarios

Vamos a utilizar ficheros ldif para agregar usuarios.

- Crear el Fichero mazinger-add.ldif con la información para crear el usuario mazinger.

![](./png/3.2contenido.png)



- ldapadd -x -W -D "cn=Directory Manager" -f mazinger-add.ldif , escribir los datos del fichero anterior en LDAP.

![](./png/3.2comprobar.png)



# Comprobar el nuevo usuario

Para listar los usuarios de un directorio, podemos filtrar por "(uid=*)", ya que estamos usando la clase posixAccount.


- ldapsearch -W -D "cn=Directory Manager" -b "dc=ldapXX,dc=curso2021" "(uid=*)", para comprobar si se ha creado el usuario correctamente en el LDAP.

![](./png/3.3comprobacion.png)


# 4. Contraseñas encriptadas

En el ejemplo anterior la clave se puso en texto plano. Cualquiera puede leerlo y no es seguro. Vamos generar valores de password encriptados.


# Generar clave encriptada SHA.

- Ejecutar zypper in openldap2, para instalar la heramienta slappasswd en OpenSUSE.

![](./png/4.1.png)


# Agregar más usuarios con clave encriptada

![](./png/add4.2.png)

# Comprobar los usuarios creados

- En el cliente.


- nmap -Pn IP-LDAP-SERVER, comprobar que el puerto LDAP del servidor está abierto.

![](./png/4.3.1.png)


- ldpasearch -H ldap:///IP-LDAP-SERVER -W -D "cn=Directory Manager" -b "dc=ldapXX,dc=curso2021" "(uid=*)" | grep dn para consultar los usuarios LDAP que tenemos en el servicio de directorio remoto.

![](./png/4.3.2.png)

#Acceso Remoto VNC.

![](./png/logo.png)

                                  Gontran Pestana Fernández - 2ºASIR - P1.


# 1.Windows Slave VNC

- Configurar la máquina virtual siguiendo los pasos del documento entregado y configurar su direccionamiento IP.

## Configuración IP para Windows 7 slave.
![](./png/ipslave.png)


- Descargar programa ThightVNC e instalarlo con la siguiente configuración.

## Configuración de la instalacioón de TightVNC.

![](./png/1slave.png)


- Permitir en la configuración del cortafuegos el servidor TightVNC.

## Revisar la configuración del cortafuegos.

![](./png/2slave.png)


# 2.Windows Master VNC.

- Configurar la máquina virtual siguiendo los pasos del documento entregado y configurar su direccionamiento IP en estático.

## Configuración IP para Windows 7 Master.

![](./png/ipmaster.png)


- Descargar el programa ThightVNC (https://www.tightvnc.com/download.php) e instalarlo igual que en la imagen.

## Configuración de la instalacioón de TightVNC.

![](./png/1master.png)


- Permitir el servidor TightVNC para el Windows Master.

## Revisar la configuración del cortafuegos.

![](./png/2master.png)


# 3.Comprobación final

- Funcionamiento del servicio TightVNC en Windows Slave desde Windows Master.

![](./png/3slave.png)

* Conexión
![](./png/2.1.1.png)


- Funcionamiento del servicio TightVNC en Windows Master desde OpenSuse/Linux master.

![](./png/3master.png)

* Conexión:
![](./png/2.1.2.png)

- Funcionamiento del comando netstat -n desde el servidor.

![](./png/2.1.3.png)

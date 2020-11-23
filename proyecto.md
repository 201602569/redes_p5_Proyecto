

## Proyecto Redes de Computadoras 
## 201602569 Christopher Soto

# Manual de Configuracion
>
### Descripcion de la Topologia utilizada 
#### Topologia 1
> ![](/PRO%20TOPO1/Topo.png)
> Descripcion:
> la siguiente topologia muestra la estructura de 
>   cliente-distribucion-nucleo
> la cual nos permite ver como se distribuira de una mejor manera la carga entre los clientes
> la topologia comienza con una nube que se conecta a un router inicial, este router se conecta a
> los dos nucleos, los cuales tienen que conectarse a los dos etherswitch de distribucion que son los 
> que van a hacer la distribucion de paquetes, luego estos distribuidores se conectan a switches
> los cuales ya llevan la conexion hasta la capa de los clientes donde ya se puede acceder a la red
>
>
>

## configuracion de distribucio 1
>
>en el etherswitch1 se configuran las vlans por medio de los comandos vlan # donde el numeral es el
>numero de vlan correpondiente luego colocamos name "nombre" donde le colocamos nombre a las vlans
>
>
>posteriormente configuramos los puertos de modo trunk
>
> ![](/PRO%20TOPO1/distribucion1.png)
## configuracion de distribucio 2
>
>en el etherswitch1 se configuran las vlans por medio de los comandos vlan # donde el numeral es el
>numero de vlan correpondiente luego colocamos name "nombre" donde le colocamos nombre a las vlans
>
>
>posteriormente configuramos los puertos de modo trunk
>
> ![](/PRO%20TOPO1/distribucion2.png)

## configuracion de switches
>
> para configurar los switchs utilizamos la misma configuracion en ambos
> colocamos en modo dot1q el puerto 0
> colocamos la vlan 20 al puerto1 y la vlan 50 al puerto 2
>
> ![](/PRO%20TOPO1/switch.png)
## configuracion de clientes
> para la configuracion de los clientes les asignaremos ip a cada uno y probaremos que sea necesario >el envio de paquetes entre ellas.
> ![](/PRO%20TOPO1/cliente10.png)
> ![](/PRO%20TOPO1/cliente30.png)
> ![](/PRO%20TOPO1/cliente40.png)
#### Topologia 2

## configuracion de switch
>
> se utiliza la misma configuracion que la topo1
> ![](/TOPO%202%20P5/switch.png)
>
>
# Manual de Comandos

#### Topologia 1
>conf t 
>int range f0/0 - 1
>no shu
>exit
>
>int f0/0.1
>encapsulation dot1Q 42
>ip address 192.168.10.254 255.255.255.0
>exit
>
>int f0/0.2
>encapsulation dot1Q 52
>ip address 192.168.20.254 255.255.255.0
>exit
>
>int f0/0.3
>encapsulation dot1Q 62
>ip address 192.168.30.254 255.255.255.0
>exit
>
>int f0/0.4
>encapsulation dot1Q 72
>ip address 192.168.40.254 255.255.255.0
>exit
>
>int f0/1.1
>encapsulation dot1Q 42
>ip address 192.168.10.254 255.255.255.0
>exit
>
>int f0/1.2
>encapsulation dot1Q 52
>ip address 192.168.20.254 255.255.255.0
>exit
>
>int f0/1.3
>encapsulation dot1Q 62
>ip address 192.168.30.254 255.255.255.0
>exit
>
>int f0/1.4
>encapsulation dot1Q 72
>ip address 192.168.40.254 255.255.255.0
>exit
#### Topologia 2
>
>EtherSwitch
>conf t: accede a las configuraciones de algun terminal
>vlan #:  permite crear una vlan indicandole el número de esta
>name : nos permite crear un nombre para nuestra VLAN
>int f#/#: nos permite ingresar a alguna de nuestras interfaces donde los # indicaran a que interface 
>switchport mode trunk: convierte un puerto de nuestro etherswitch en modo trunk que este nos permite 
>no shut: Este es el comando que habilita una interfaz.
>Comandos de router
>int range f#/# - #:  entra a un rango para la configuracion de las interfaces donde # es el >número de no shu: Este es el comando que habilita una interfaz.
>exit Este sirve para salir de la configuracion actual.
>
>int f#/#.#: sirve para configurar una sub interfaz.

# paquetes
> para verificar que los pings estan siendo correctos procedemos a verificar la captura de los paquetes
> ![](/PRO%20TOPO1/paquetespr.png)

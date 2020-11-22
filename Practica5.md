## Practica 5 Redes de Computadoras 
## 201602569 Christopher Soto

# Manual de Configuracion
>
### Descripcion de la Topologia utilizada 
#### Topologia 1
> ![](/TOPO1%20P5/topologia.png)
> Descripcion:
> La topologia cuenta con cuatro clientes, los cuales se conectan a dos switches,
>    -cliente 1 y 2 a switch 1
>    -cliente 3 y 4 a switch 2
>
> Ambos switches van conectados a un ethernetswitch el cual se conecta al router que va
> conectado a la nuve que interconectara ambas topologias.
>
>
>
## configuracion de etherswitch
>
>en el etherswitch1 se configuran las vlans por medio de los comandos vlan # donde el numeral es el
>numero de vlan correpondiente luego colocamos name "nombre" donde le colocamos nombre a las vlans
>
>
>posteriormente configuramos los puertos de modo trunk
>
> ![](/TOPO1%20P5/eter1.png)
>
> ![](/TOPO1%20P5/eter.png)

## configuracion de routers
>
>Router 1
>dentro del router 1 configuramos las diferentes subinterfaces por medio de los comandos 
> int f#/#.# donde los primeros 2 numerales corresponden a los puertos y el ultimo a la vlan
> luego configuramos las ip y las mascaras correspondientes
>
> ![](/TOPO1%20P5/router1.png)
## configuracion de switches
>
> para configurar los switchs utilizamos la misma configuracion en ambos
> colocamos en modo dot1q el puerto 0
> colocamos la vlan 20 al puerto1 y la vlan 50 al puerto 2
>
> ![](/TOPO1%20P5/switch.png)
## configuracion de clientes
> para la configuracion de los clientes les asignaremos ip a cada uno y probaremos que sea necesario >el envio de paquetes entre ellas.
> ![](/TOPO1%20P5/cliente1.png)
> ![](/TOPO1%20P5/cliente2.png)
> ![](/TOPO1%20P5/tini.png)
#### Topologia 2

> ![](/TOPO%202%20P5/topo.png)

> Descripcion:
> cuenta con dos clientes, ambos conectados a un switch
>   -cliente1 a switch 4
>   -cliente2 a switch 5
>
> ambos switchs se conectan a un ethernet switch que se conecta a dos routers (3-4)
>
> luego estos dos routers se conectan al ultimo router de la topologia que va conectado a la nuve.


# Manual de Comandos

#### Topologia 1
>conf t 
>int range f0/0 - 1
>no shu
>exit
>
>int f0/0.1
>encapsulation dot1Q 20
>ip address 192.168.10.254 255.255.255.0
>exit
>
>int f0/0.2
>encapsulation dot1Q 30
>ip address 192.168.20.254 255.255.255.0
>exit
>
>int f0/0.3
>encapsulation dot1Q 40
>ip address 192.168.30.254 255.255.255.0
>exit
>
>int f0/0.4
>encapsulation dot1Q 50
>ip address 192.168.40.254 255.255.255.0
>exit
>
>int f0/1.1
>encapsulation dot1Q 20
>ip address 192.168.10.254 255.255.255.0
>exit
>
>int f0/1.2
>encapsulation dot1Q 30
>ip address 192.168.20.254 255.255.255.0
>exit
>
>int f0/1.3
>encapsulation dot1Q 40
>ip address 192.168.30.254 255.255.255.0
>exit
>
>int f0/1.4
>encapsulation dot1Q 50
>ip address 192.168.40.254 255.255.255.0
>exit
>
>
>
#### Topologia 2
>========================EIGRP=========================
>
>
>------------------------R2----------------------------
>
>conf t
>
>router eigrp 10
>
>network 10.10.0.0 0.0.0.255
>
>network 20.10.0.0 0.0.0.255
>
>network 192.168.15.0 0.0.0.255
>
>end
>
>------------------------R3----------------------------
>conf t
>
>router eigrp 10
>
>network 10.10.0.0 0.0.0.255
>
>network 20.10.0.0 0.0.0.255
>
>network 192.168.15.0 0.0.0.255
>
>end
>
>------------------------R4----------------------------
>
>conf t
>
>router eigrp 10
>
>network 10.10.0.0 0.0.0.255
>
>network 20.10.0.0 0.0.0.255
>
>network 192.168.15.0 0.0.0.255
>
>end
>
>========================VRRP===========================
>
>------------------------R3----------------------------
>conf t
>
>vrrp 10
>
>vrrp 10 ip 192.168.15.3
>
>vrrp 10 priority 120
>
>vrrp 10 preempt
>
>end
>
>------------------------R4----------------------------
>conf t
>
>vrrp 10
>
>vrrp 10 ip 192.168.15.3
>
>vrrp 10 priority 100
>
>end
>
>========================INTERFACES===========================
>
>------------------------ESW2----------------------------
>
>conf t
>
>int range f1/0 - 3
>
>no shut
>
>end




# paquetes
> para verificar que los pings estan siendo correctos procedemos a verificar la captura de los paquetes
> ![](/TOPO1%20P5/paquetes5.png)

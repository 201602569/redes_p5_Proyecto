## Practica 5 Redes de Computadoras 
## 201602569 Christopher Soto

# Manual de Configuracion
>
### Descripcion de la Topologia utilizada 
#### Topologia 1
> ![](/TOPO1%20P5/topologia.png)
> Descripcion:
> La topologia esta realizada para una empresa la cual tiene 3 departamentos
> 1. Finanzas
> 2. Ventas
> 2. Informatica
>
> La parte de Finanzas consta de dos computadoras (VPC1,VPC2) que estan conectadas a un switch (SWITCH1)
> este esta conectado a un router que sera al que todos los departamentos estan conectados.
>
> La parte de Ventas consta de tres computadoras (VPC3,VPC4,VPC5) que estan conectadas a un switch (SWITCH2)
> este esta conectado a un router que sera al que todos los departamentos estan conectados.
>
> La parte de Informatica consta de una computadora (maquina virtual tinylinux) que esta conectada a un switch (SWITCH3)
> este esta conectado a un router que sera al que todos los departamentos estan conectados.
>

#### Topologia 2

> ![](/TOPO%202%20P5/topo.png)

> Descripcion:
> La topologia esta realizada para una empresa la cual tiene 3 departamentos
> 1. Finanzas
> 2. Ventas
> 2. Informatica
>
> La parte de Finanzas consta de dos computadoras (VPC1,VPC2) que estan conectadas a un switch (SWITCH1)
> este esta conectado a un router que sera al que todos los departamentos estan conectados.
>
> La parte de Ventas consta de tres computadoras (VPC3,VPC4,VPC5) que estan conectadas a un switch (SWITCH2)
> este esta conectado a un router que sera al que todos los departamentos estan conectados.
>
> La parte de Informatica consta de una computadora (maquina virtual tinylinux) que esta conectada a un switch (SWITCH3)
> este esta conectado a un router que sera al que todos los departamentos estan conectados.
>




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
>router eigrp 10
>network 10.10.0.0 0.0.0.255
>network 20.10.0.0 0.0.0.255
>network 192.168.15.0 0.0.0.255
>end
>
>------------------------R4----------------------------
>conf t
>router eigrp 10
>network 10.10.0.0 0.0.0.255
>network 20.10.0.0 0.0.0.255
>network 192.168.15.0 0.0.0.255
>end
>
>========================VRRP===========================
>
>------------------------R3----------------------------
>conf t
>vrrp 10
>vrrp 10 ip 192.168.15.3
>vrrp 10 priority 120
>vrrp 10 preempt
>end
>
>------------------------R4----------------------------
>conf t
>vrrp 10
>vrrp 10 ip 192.168.15.3
>vrrp 10 priority 100
>end
>
>========================INTERFACES===========================
>------------------------ESW2----------------------------
>conf t
>int range f1/0 - 3
>no shut
>end




# paquetes
> ![](/TOPO1%20P5/paquetes5.png)

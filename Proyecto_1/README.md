# Proyecto 1
## Redes de Computadoras 2
## Grupo 20
Eduardo Ismael Llamas Calderón (200530614)

José Fernando Recinos Acuté (201114236)

# Topología

![Topología](/Proyecto_1/image/topologia.png)

# Configuración de Multi Switch - CORE

## Configuración de MSW1

```plaintext
hostname MSW1
!
interface GigabitEthernet1/0/1
 switchport access vlan 17
 switchport mode access
!
interface GigabitEthernet1/0/2
 switchport access vlan 16
 switchport mode access
!
interface GigabitEthernet1/0/1
 switchport access vlan 17
 switchport mode access
!
interface GigabitEthernet1/0/2
 switchport access vlan 16
 switchport mode access
!
interface GigabitEthernet1/1/1
 switchport mode trunk
!
interface GigabitEthernet1/1/2
 switchport mode trunk
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan16
 mac-address 00e0.f9b2.0201
 ip address 172.16.20.17 255.255.255.240
!
interface Vlan17
 mac-address 00e0.f9b2.0202
 ip address 172.17.20.17 255.255.255.240
!
interface Vlan50
 mac-address 00e0.f9b2.0203
 ip address 20.50.0.1 255.255.255.252
!
interface Vlan60
 mac-address 00e0.f9b2.0204
 ip address 20.60.0.1 255.255.255.252
!
router eigrp 10
 network 172.16.20.16 0.0.0.15
 network 20.50.0.0 0.0.0.3
 network 20.60.0.0 0.0.0.3
 network 172.17.20.16 0.0.0.15
 auto-summary
!
interface Vlan10
 mac-address 00e0.8f08.9901
 ip address 172.20.0.1 255.255.255.252
!
interface Vlan20
 mac-address 00e0.8f08.9902
 ip address 172.20.0.5 255.255.255.252
!
interface Vlan30
 mac-address 00e0.8f08.9903
 ip address 20.20.0.1 255.255.255.252
!
interface Vlan40
 mac-address 00e0.8f08.9904
 ip address 20.20.0.5 255.255.255.252
!
router eigrp 10
 network 172.20.0.0 0.0.0.3
 network 172.20.0.4 0.0.0.3
 network 20.20.0.0 0.0.0.3
 network 20.20.0.4 0.0.0.3
 auto-summary

vtp version 2
vtp domain usac
vtp mode server 

```

## CORE - Conexión entre edificios
### InterVLAN


| VLAN |     Nombre    |    Dirección IP   | Máscara de Subred |
|------|---------------|-------------------|-------------------|
|  16  |      T16      |    172.16.20.17   | 255.255.255.240   |
|  17  |      T17      |    172.17.20.17   | 255.255.255.240   |
|  50  |    VLAN0050   |     20.50.0.1     | 255.255.255.252   |
|  60  |    VLAN0060   |     20.60.0.1     | 255.255.255.252   |


## Configuración de MSW2

```plaintext
hostname MSW2
!
spanning-tree mode pvst
!
interface Port-channel1
 switchport mode trunk
!
interface GigabitEthernet1/0/1
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/0/2
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/0/3
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/1/1
 switchport mode trunk
!
interface GigabitEthernet1/1/2
 switchport mode trunk
!
interface GigabitEthernet1/1/3
 switchport mode trunk
!
interface Vlan20
 mac-address 00d0.ff47.9c01
 ip address 192.168.20.5 255.255.255.0
 ip helper-address 172.17.20.18
!
interface Vlan21
 mac-address 00d0.ff47.9c02
 ip address 192.168.21.5 255.255.255.0
 ip helper-address 172.17.20.18
!
interface Vlan50
 mac-address 00d0.ff47.9c03
 ip address 20.50.0.2 255.255.255.252
!
interface Vlan70
 mac-address 00d0.ff47.9c04
 ip address 20.70.0.2 255.255.255.252
!
interface Vlan80
 mac-address 00d0.ff47.9c05
 ip address 20.80.0.2 255.255.255.252
!
router eigrp 10
 network 20.50.0.0 0.0.0.3
 network 20.70.0.0 0.0.0.3
 network 20.80.0.0 0.0.0.3
 network 192.168.20.0
 network 192.168.21.0
 auto-summary
!

```

### VLAN


| VLAN |     Nombre    |    Dirección IP   | Máscara de Subred |
|------|---------------|-------------------|-------------------|
|  20  |    VLAN0020   |    192.168.20.5   |   255.255.255.0   |
|  21  |    VLAN0021   |    192.168.21.5   |   255.255.255.0   |
|  50  |    VLAN0050   |     20.50.0.2     |  255.255.255.252  |
|  70  |    VLAN0070   |     20.70.0.2     |  255.255.255.252  |
|  80  |    VLAN0080   |     20.80.0.2     |  255.255.255.252  |


## Configuración de MSW3

```plaintext
hostname MSW3
!
spanning-tree mode pvst
!
interface Port-channel2
 switchport mode trunk
!
interface GigabitEthernet1/0/1
 switchport mode trunk
 channel-group 2 mode active
!
interface GigabitEthernet1/0/2
 switchport mode trunk
 channel-group 2 mode active
!
interface GigabitEthernet1/0/3
 switchport mode trunk
 channel-group 2 mode active
!
interface GigabitEthernet1/1/1
 switchport mode trunk
!
interface GigabitEthernet1/1/2
 switchport mode trunk
!
interface GigabitEthernet1/1/3
 switchport mode trunk
!
interface Vlan20
 mac-address 0003.e4db.6d01
 ip address 192.17.20.5 255.255.255.0
 ip helper-address 172.16.20.18
!
interface Vlan21
 mac-address 0003.e4db.6d02
 ip address 192.17.21.5 255.255.255.0
 ip helper-address 172.16.20.18
!
interface Vlan60
 mac-address 0003.e4db.6d03
 ip address 20.60.0.2 255.255.255.252
!
interface Vlan70
 mac-address 0003.e4db.6d04
 ip address 20.70.0.1 255.255.255.252
!
interface Vlan90
 mac-address 0003.e4db.6d05
 ip address 20.90.0.1 255.255.255.252
!
router eigrp 10
 network 20.60.0.0 0.0.0.3
 network 20.70.0.0 0.0.0.3
 network 20.90.0.0 0.0.0.3
 network 192.17.20.0
 network 192.17.21.0
 auto-summary
!

```

### VLAN

| VLAN |     Nombre    |    Dirección IP   | Máscara de Subred |
|------|---------------|-------------------|-------------------|
|  20  |    VLAN0020   |    192.17.20.5    |   255.255.255.0   |
|  21  |    VLAN0021   |    192.17.21.5    |   255.255.255.0   |
|  60  |    VLAN0060   |     20.60.0.2     |  255.255.255.252  |
|  70  |    VLAN0070   |     20.70.0.1     |  255.255.255.252  |
|  90  |    VLAN0090   |     20.90.0.1     |  255.255.255.252  |


## Configuración de MSW4

```plaintext
hostname MSW4
!
spanning-tree mode pvst
!
interface GigabitEthernet1/0/1
 switchport access vlan 40
 switchport mode access
!
interface GigabitEthernet1/1/1
 switchport mode trunk
!
interface GigabitEthernet1/1/2
 switchport mode trunk
!
interface Vlan40
 mac-address 00e0.f9e4.3e01
 ip address 172.40.0.1 255.255.0.0
!
interface Vlan80
 mac-address 00e0.f9e4.3e02
 ip address 20.80.0.1 255.255.255.252
!
interface Vlan90
 mac-address 00e0.f9e4.3e03
 ip address 20.90.0.2 255.255.255.252
!
router eigrp 10
 network 20.80.0.0 0.0.0.3
 network 20.90.0.0 0.0.0.3
 network 172.40.0.0
 auto-summary
!
```

### VLAN

| VLAN |     Nombre    |    Dirección IP   | Máscara de Subred |
|------|---------------|-------------------|-------------------|
|  40  |    VLAN0040   |    172.40.0.1     |    255.255.0.0    |
|  80  |    VLAN0080   |    20.80.0.1      |  255.255.255.252  |
|  90  |    VLAN0090   |    20.90.0.2      |  255.255.255.252  |


# Configuraciones generales 

## Protocolo de enrutamiento - EIGRP

Se configuró EIGRP en los siguientes dispositivos:

### MSW1

```plaintext
router eigrp 10
 network 172.16.20.16 0.0.0.15
 network 20.50.0.0 0.0.0.3
 network 20.60.0.0 0.0.0.3
 network 172.17.20.16 0.0.0.15
 auto-summary
!
```

### MSW2

```plaintext
router eigrp 10
 network 20.50.0.0 0.0.0.3
 network 20.70.0.0 0.0.0.3
 network 20.80.0.0 0.0.0.3
 network 192.168.20.0
 network 192.168.21.0
 auto-summary
!
```

### MSW3

```plaintext
router eigrp 10
 network 20.60.0.0 0.0.0.3
 network 20.70.0.0 0.0.0.3
 network 20.90.0.0 0.0.0.3
 network 192.17.20.0
 network 192.17.21.0
 auto-summary
!
```

### MSW4

```plaintext
router eigrp 10
 network 20.80.0.0 0.0.0.3
 network 20.90.0.0 0.0.0.3
 network 172.40.0.0
 auto-summary
!
```

## LACP

Se configuró LACP en LMSW1, MSW2, MSW3, RMSW1.

## Channel 1

### MSW2 

```plaintext
interface Port-channel1
 switchport mode trunk
!
interface GigabitEthernet1/0/1
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/0/2
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/0/3
 switchport mode trunk
 channel-group 1 mode active
!
```

### LMSW1

```plaintext
interface Port-channel1
 switchport trunk encapsulation dot1q
 switchport mode trunk
!
interface FastEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 1 mode passive
!
interface FastEthernet0/2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 1 mode passive
!
interface FastEthernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 1 mode passive
 !
 ```

 ## Channel 2

 ### MSW3

```plaintext
interface Port-channel2
 switchport mode trunk
!
interface GigabitEthernet1/0/1
 switchport mode trunk
 channel-group 2 mode active
!
interface GigabitEthernet1/0/2
 switchport mode trunk
 channel-group 2 mode active
!
interface GigabitEthernet1/0/3
 switchport mode trunk
 channel-group 2 mode active
!
```

### RMSW1

```plaintext
interface Port-channel2
 switchport trunk encapsulation dot1q
 switchport mode trunk
!
interface FastEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 2 mode passive
!
interface FastEthernet0/2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 2 mode passive
!
interface FastEthernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 2 mode passive
!
```

## HSRP

### MSW2L

```plaintext
interface Vlan20
 mac-address 0001.c920.2a01
 ip address 172.168.20.1 255.255.255.0
 ip helper-address 172.17.20.18
 standby 20 ip 172.168.20.101
 standby 20 priority 150
 standby 20 preempt
!
interface Vlan21
 mac-address 0001.c920.2a02
 ip address 172.168.21.1 255.255.255.0
 ip helper-address 172.17.20.18
 standby 20 ip 172.168.21.101
 standby 20 preempt
!
```

### MSW3L

```plaintext
interface Vlan20
 mac-address 0010.1176.3901
 ip address 172.168.20.2 255.255.255.0
 ip helper-address 172.17.20.18
 standby 20 ip 172.168.20.101
!
interface Vlan21
 mac-address 0010.1176.3902
 ip address 172.168.21.2 255.255.255.0
 ip helper-address 172.17.20.18
 standby 20 ip 172.168.21.101
!
```

# Configuración de VLANs

## Mode Trunk

Todas las interfaces de los switchs capa 3 y las interfaces de los switchs capa 2 que se conectan con un switch capa 3 se configuraron con MODE TRUNK, las demás interfaces de los switchs capa 2 se configuraron con MODE ACCESS.



# Práctica 2
## Grupo 20
Eduardo Ismael Llamas Calderón (200530614)

José Fernando Recinos Acuté (201114236)

# Configuración de vlans y equipos

| Vlans         | Numero | Gateway         |
|---------------|--------|-----------------|
| CORPORATIVO   | 62     | 192.168.X.0/24  |
| VENTAS        | 12     | 1.0.0.0/ 8      |
| DISTRIBUCIÓN  | 22     | 2.0.0.0/8       |

# Configuración de vlans CORPORATIVA

| Sector        | Gateway         |
|---------------|-----------------|
| RHH           | 192.168.72.1/24 |
| SOPORTE       | 192.168.82.1/24 |
| IT            | 192.168.92.1/24 |

# Configuración de equipos

| Equipo        | Sector          | Gateway      | 
|---------------|-----------------|--------------|
| 192.168.72.2  | RHH             | 192.168.72.1 |
| 192.168.72.3  | RHH             | 192.168.72.1 |
| 192.168.72.4  | RHH             | 192.168.72.1 |
| 192.168.82.2  | SOPORTE         | 192.168.82.1 |
| 192.168.72.3  | IT              | 192.168.92.1 |
| 192.168.72.4  | IT              | 192.168.92.1 |


# Topología

![Topología](/Practica_2/image/topologia.png)

## Configuración de los Switchs 

```bash

----------------- Configuración de SW1  --------------

en
conf t
hostname SW1

vlan 62
 name CORPORATIVO
vlan 12
 name VENTAS
vlan 22
 name DISTRIBUCION
vlan 999
 name BLACKHOLE
vlan 99
 name NATIVA

interface range FastEthernet0/6 - 24
 switchport mode access
 switchport access vlan 999
 shutdown

interface range FastEthernet0/1 - 2
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
 channel-group 2 mode passive
 no shutdown

interface range FastEthernet0/3 - 5
 switchport mode access
 switchport access vlan 62
 no shutdown

interface Port-channel2
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
end


write


----------------- Configuración de MSW1  --------------
en
conf t
host MSW1
ip routing 

vlan 62
name CORPORATIVO
vlan 12
name VENTAS
vlan 22
name DISTRIBUCION
vlan 999
name BLACKHOLE
exit

interface Port-channel2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22



int range fa0/1-2
switchport trunk encapsulation dot1q
switchport mode trunk 
switchport trunk native vlan 99
switchport trunk allowed vlan 99,62,12,22
channel-group 2 mode active
no shut

interface GigabitEthernet0/1
description connection to MSW4
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 99,62,12,22
no shutdown

interface range FastEthernet0/3 - 24
switchport mode access
switchport access vlan 999
shutdown

interface GigabitEthernet0/2
switchport mode access
switchport access vlan 999
shutdown

int vlan 62
description Default Gateway SVI for 192.168.72.0/24
ip add 192.168.72.1 255.255.255.0
no shut

int vlan 12
description Default Gateway SVI for 1.0.0.0/8
ip add 1.0.0.1 255.0.0.0
no shut
exit

router eigrp 100
network 192.168.72.0 0.0.0.255
network 1.0.0.0 0.255.255.255

end

write

----------------- Configuración de SW2  --------------


en
conf t
hostname SW2

vlan 62
 name CORPORATIVO
vlan 12
 name VENTAS
vlan 22
 name DISTRIBUCION
vlan 999
 name BLACKHOLE
vlan 99
 name NATIVA

interface range FastEthernet0/4 - 24
 switchport mode access
 switchport access vlan 999
 shutdown

interface range FastEthernet0/1 - 2
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
 no shutdown

interface FastEthernet0/3
 switchport mode access
 switchport access vlan 62
 no shutdown

interface Port-channel1
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
end


write



----------------- Configuración de MSW4  --------------

en
conf t
host MSW1
ip routing 

vlan 62
name CORPORATIVO
vlan 12
name VENTAS
vlan 22
name DISTRIBUCION
vlan 999
name BLACKHOLE
exit

interface Port-channel1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22


int range fa0/1-2
switchport trunk encapsulation dot1q
switchport mode trunk 
switchport trunk native vlan 99
switchport trunk allowed vlan 99,62,12,22
channel-group 1 mode active
no shut

interface GigabitEthernet0/1
 description connection to MSW2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
 no shutdown


interface GigabitEthernet0/2
 description connection to MSW7
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
 no shutdown

interface range FastEthernet0/3 - 24
switchport mode access
switchport access vlan 999
shutdown

interface vlan 62
description Default Gateway SVI for 192.168.82.0/24
ip add 192.168.82.1 255.255.255.0
no shut

interface vlan 12
description Default Gateway SVI for 1.0.0.0/8
ip add 1.0.0.2 255.0.0.0
no shut

interface vlan 22
description Default Gateway SVI for 2.0.0.0/8
ip add 2.0.0.2 255.0.0.0
no shut
exit

router eigrp 100
 network 192.168.82.0 0.0.0.255
 network 1.0.0.0 0.255.255.255
 network 2.0.0.0 0.255.255.255


router ospf 1
 network 192.168.82.0 0.0.0.255 area 0
 network 2.0.0.0 0.255.255.255 area 0
end

write


----------------- Configuración de SW3  --------------


en
conf t
hostname SW1

vlan 62
 name CORPORATIVO
vlan 12
 name VENTAS
vlan 22
 name DISTRIBUCION
vlan 999
 name BLACKHOLE
vlan 99
 name NATIVA

interface range FastEthernet0/5 - 24
 switchport mode access
 switchport access vlan 999
 shutdown

interface range FastEthernet0/1 - 2
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
 no shutdown

interface range FastEthernet0/3 - 4
 switchport mode access
 switchport access vlan 62
 no shutdown

interface Port-channel3
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
end


write


----------------- Configuración de MSW7  --------------
en
conf t
host MSW7
ip routing 

vlan 62
name CORPORATIVO
vlan 12
name VENTAS
vlan 22
name DISTRIBUCION
vlan 999
name BLACKHOLE
exit

interface Port-channel3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22


int range fa0/1-2
switchport trunk encapsulation dot1q
switchport mode trunk 
switchport trunk native vlan 99
switchport trunk allowed vlan 99,62,12,22
channel-group 3 mode active
no shut

interface GigabitEthernet0/2
 description connection to MSW4
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 99,62,12,22
 no shutdown


interface GigabitEthernet0/1
shutdown

interface range FastEthernet0/3 - 24
switchport mode access
switchport access vlan 999
shutdown

interface vlan 62
description Default Gateway SVI for 192.168.92.0/24
ip add 192.168.92.1 255.255.255.0
no shut

interface vlan 22
description Default Gateway SVI for 2.0.0.0/8
ip add 2.0.0.1 255.0.0.0
no shut
exit

router eigrp 100
 network 192.168.82.0 0.0.0.255
 network 1.0.0.0 0.255.255.255
 network 2.0.0.0 0.255.255.255


router ospf 1
 network 192.168.82.0 0.0.0.255 area 0
 network 2.0.0.0 0.255.255.255 area 0
end

write

```
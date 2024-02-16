# Práctica 1
## Grupo 20
Eduardo Ismael Llamas Calderón (200530614)

José Fernando Recinos Acuté (201114236)

# Configuración de vlans y equipos

| Vlans         | Numero | Gateway         |
|---------------|--------|-----------------|
| Primaria      | 12     | 192.168.12.0/24 |
| Basico        | 22     | 192.168.22.0/24 |
| Diversificado | 32     | 192.168.32.0/24 |

### Equipos VLAN 10
- 192.168.12.10 255.255.255.0
- 192.168.12.11 255.255.255.0
- 192.168.12.12 255.255.255.0
- 192.168.12.13 255.255.255.0

### Equipos VLAN 20
- 192.168.22.10 255.255.255.0
- 192.168.22.11 255.255.255.0

### Equipos VLAN 30
- 192.168.32.10 255.255.255.0
- 192.168.32.11 255.255.255.0
- 192.168.32.12 255.255.255.0
- 192.168.32.13 255.255.255.0

# Topología

![Topología](/Practica1/topologia.png)

# Configuración de Switch Capa 2 en Cisco Packet Tracer

## Configuración de los Switchs 

```bash

---------------------------------- Switch 1 ------------------------------------

en
conf t
hostname SW1_G20
vtp version 2
vtp mode server
vtp domain g20
vtp password usac

vlan 12
name primaria
vlan 22
name basicos
vlan 32
name diversificado
vlan 1000
name nativa
vlan 999
name blackhole

interface range FastEthernet0/1 - 5
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate

interface range FastEthernet0/6 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown
end
write

Seguridad con password secreto

enable secret redes2grupo20
line console 0
password redes2grupo20
login
line vty 0 15
password redes2grupo20
login
exit
service password-encryption

---------------------------------- Switch 2 ------------------------------------
en
conf t
hostname SW2_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 5
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate


interface range FastEthernet0/6 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown
end
write

---------------------------------- Switch 3 ------------------------------------
en
conf t
hostname SW3_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 5
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate


interface range FastEthernet0/6 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown
end
write

---------------------------------- Switch 4 ------------------------------------

en
conf t
hostname SW4_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 5
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate



interface range FastEthernet0/6 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown
end
write

---------------------------------- Switch 5 ------------------------------------

en
conf t
hostname SW5_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 5
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate


interface range FastEthernet0/6 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown
end
write

---------------------------------- Switch 6 ------------------------------------

en
conf t
hostname SW6_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 5
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate


interface range FastEthernet0/6 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown
end
write

---------------------------------- Switch 7 ------------------------------------

en
conf t
hostname SW7_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 2
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate

interface range FastEthernet0/5 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown

interface FastEthernet0/3
switchport mode access
switchport access vlan 12
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0003.E4BC.22D7


interface FastEthernet0/4
switchport mode access
switchport access vlan 12
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0090.21A8.AA13

end
write

---------------------------------- Switch 8 ------------------------------------

en
conf t
hostname SW8_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 2
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate

interface range FastEthernet0/4 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown

interface FastEthernet0/3
switchport mode access
switchport access vlan 22
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0060.2F8A.04A5

end
write

---------------------------------- Switch 9 ------------------------------------

en
conf t
hostname SW9_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 2
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate

interface range FastEthernet0/5 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown

interface range FastEthernet0/3
switchport mode access
switchport access vlan 32
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0006.2AB2.6EC5


interface range FastEthernet0/4
switchport mode access
switchport access vlan 32
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0001.962D.3AA6

end
write

---------------------------------- Switch 10 ------------------------------------

en
conf t
hostname SW10_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 2
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate


interface range FastEthernet0/5 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown

interface range FastEthernet0/3
switchport mode access
switchport access vlan 32
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0007.EC6E.AAAA


interface range FastEthernet0/4
switchport mode access
switchport access vlan 32
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0003.E438.739C

end
write

---------------------------------- Switch 11 ------------------------------------

en
conf t
hostname SW11_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 2
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate

interface range FastEthernet0/4 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown

interface FastEthernet0/3
switchport mode access
switchport access vlan 22
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0001.633B.9078

end
write

---------------------------------- Switch 12 ------------------------------------

en
conf t
hostname SW12_G20
vtp version 2
vtp mode client
vtp domain g20
vtp password usac

interface range FastEthernet0/1 - 2
switchport mode trunk
switchport trunk native vlan 1000
switchport trunk allowed vlan 12,22,32,1000
switchport nonegotiate


interface range FastEthernet0/5 - 24
switchport mode access
switchport access vlan 999
shutdown

interface range GigabitEthernet0/1 - 2
switchport mode access
switchport access vlan 999
shutdown

interface range FastEthernet0/3
switchport mode access
switchport access vlan 12
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 00E0.8F72.9409


interface range FastEthernet0/4
switchport mode access
switchport access vlan 12
switchport nonegotiate
switchport port-security
switchport port-security violation shutdown
switchport port-security maximum 1
switchport port-security mac-address 0001.63EA.88D0

end
write

------------------------------------------------------------------------


```
## Configuración de spanning-tree protocol en todos los switch

```bash

en
conf t
spanning-tree mode rapid-pvst
spanning-tree vlan 12,22,32,1000 root primary
end
write

```

## Analisis de configuración de spanning-tree protocol

| Escenario | Protocolo Spanning-tree | Red Primaria | Red Básicos | Red Diversificado |
|-----------|-------------------------|--------------|-------------|-------------------|
| 1         | PVST                    | 47           | 68          | 65                |
| 2         | Rapid PVST              | 40           | 43          | 38                |

- Validación de RPVST

## Red Primaria

- **Ping 192.162.12.10 a 192.168.12.13**
  - Ruta: PC1 -> SW7 -> SW4 -> SW2 -> SW6 -> SW12
  - Tiempo:
    - PSVT: 47
    - RPVST: 40

## Red Basicos

- **Ping 192.168.22.10 a 192.168.12.11**
  - Ruta: PC3 -> PC8 -> SW8 -> SW4 -> SW2 -> SW6 -> SW11
  - Tiempo:
    - PSVT: 68
    - RPVST: 43

## Red Diversificado
- **Ping 192.168.22.10 a 192.168.12.11**
  - Ruta: PC3 -> PC8 -> SW9 -> SW4 -> SW2 -> SW6 -> SW10
  - Tiempo:
    - PSVT: 65
    - RPVST: 38



## Asignación de direcciones MAC a las PCs
+ PC1: 0003.E4BC.22D7
+ PC2: 0090.21A8.AA13
+ PC3: 0060.2F8A.04A5
+ PC4: 0006.2AB2.6EC5
+ PC5: 0001.962D.3AA6
+ PC6: 0007.EC6E.AAAA
+ PC7: 0003.E438.739C
+ PC8: 0001.633B.9078
+ PC9: 00E0.8F72.9409
+ PC10: 0001.63EA.88D0
# Práctica 1
## Grupo 20
Eduardo Ismael Llamas Calderón (200530614)

José Fernando Recinos Acuté (201114236)

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
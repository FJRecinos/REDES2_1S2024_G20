# Práctica 1 Configuración de Red en PNETLab
Grupo 25
Eduardo Ismael Llamas Calderón (200530614)
José Fernando Recinos Acuté (201114236)

# Configuración de Switch Capa 2 en Cisco Packet Tracer

## Configuración del Switch (SW12_G20)

```bash
conf t
host SW12_G20
vtp mode client
vtp domain G20
vtp password REDES2
vtp version 2

int range fa0/4-24
shut
exit
int range gigabitEthernet 0/1-2
shut
exit

int range fa0/1-2
switchport mode trunk
switchport trunk native vlan 99
switchport port-security 
switchport port-security maximum 5
switchport port-security mac-address sticky
switchport nonegotiate
switchport trunk allowed vlan 12,22,32
exit

int fa0/3
switchport mode access 
switchport access vlan 22
switchport port-security 
switchport port-security maximum 5
switchport port-security mac-address 0002.1744.D383
switchport nonegotiate
exit

int fa0/4
switchport mode access 
switchport access vlan 12
switchport port-security 
switchport port-security maximum 5
switchport port-security mac-address 0002.1744.D383
switchport nonegotiate
exit
```

## Asignación de direcciones MAC a las PCs
---PC1: 0009.7CEA.5A90
---PC2: 000B.BE88.960A
---PC3: 00E0.A352.D395
---PC4: 00E0.F935.52B5
---PC5: 00E0.A3DC.AD6B
---PC6: 0010.110C.1D09
---PC7: 0060.3E4B.ECAC
---PC8: 0002.1744.D383
---PC9: 000C.85D3.5A14
---PC10: 0006.2A0A.C934
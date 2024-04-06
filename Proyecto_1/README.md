# Proyecto 1
## Grupo 20
Eduardo Ismael Llamas Calderón (200530614)

José Fernando Recinos Acuté (201114236)


# Configuración de Multi Switch

## Configuración de MSW1

```plaintext
hostname MSW1
!
interface GigabitEthernet1/0/1
 switchport access vlan 10
 switchport mode access
!
interface GigabitEthernet1/0/2
 switchport access vlan 20
 switchport mode access
!
interface GigabitEthernet1/1/1
 switchport mode trunk
!
interface GigabitEthernet1/1/2
 switchport mode trunk
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

| VLAN |     Nombre    |    Dirección IP   | Máscara de Subred |
|------|---------------|-------------------|-------------------|
|  10  |      ET10     |   172.20.0.1      | 255.255.255.252   |
|  20  |      ET20     |   172.20.0.5      | 255.255.255.252   |
|  30  |      ET30     |   20.20.0.1       | 255.255.255.252   |
|  40  |      ET40     |   20.20.0.5       | 255.255.255.252   |



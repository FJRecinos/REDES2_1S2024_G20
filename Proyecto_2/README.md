# Proyecto 2
## Grupo 20
Eduardo Ismael Llamas Calderón (200530614)

José Fernando Recinos Acuté (201114236)


### Documentación para red Akado:

#### Subredes Asignadas:
- **Rostec**: 192.168.30.0/26
- **Sberbank**: 192.168.30.64/26

#### Tamaño de Subredes:
- Se utiliza una máscara de subred /26 (255.255.255.192), lo que permite hasta 62 hosts por subred.

#### Tipo de Enrutamiento Dinámico:
- Se utiliza el protocolo EIGRP para el enrutamiento dinámico en la red de Akado.

#### Tabla de Enrutamiento:
| Subnet    | Start Address   | End Address     | Network Address | Broadcast Address |
|-----------|-----------------|-----------------|-----------------|-------------------|
| Rostec    | 192.168.30.1    | 192.168.30.62   | 192.168.30.0    | 192.168.30.63     |
| Sberbank  | 192.168.30.65   | 192.168.30.126  | 192.168.30.64   | 192.168.30.127    |


### Documentación para Yota:

#### Subredes Asignadas:
- **Adif**: 192.168.40.0/26
- **Rosneft**: 192.168.40.64/26

#### Tamaño de Subredes:
- Se utiliza una máscara de subred /26 (255.255.255.192), lo que permite hasta 62 hosts por subred.

#### Tipo de Enrutamiento Dinámico:
- Se utiliza el protocolo RIP para el enrutamiento dinámico en la red de Yota.

#### Tabla de Enrutamiento:
| Subnet   | Start Address   | End Address     | Network Address | Broadcast Address |
|----------|-----------------|-----------------|-----------------|-------------------|
| Adif     | 192.168.40.1    | 192.168.40.62   | 192.168.40.0    | 192.168.40.63     |
| Rosneft  | 192.168.40.65   | 192.168.40.126  | 192.168.40.64   | 192.168.40.127    |


### Documentación para Rostelecom:

#### Subredes Asignadas:
- **Mercasa**: 192.168.70.0/26
- **Navantia**: 192.168.70.64/26

#### Tamaño de Subredes:
- Se utiliza una máscara de subred /26 (255.255.255.192), lo que permite hasta 62 hosts por subred.

#### Tipo de Enrutamiento Dinámico:
- Se utiliza el protocolo OSPF para el enrutamiento dinámico en la red de Rostelecom.

#### Tabla de Enrutamiento:
| Subnet    | Start Address   | End Address     | Network Address | Broadcast Address |
|-----------|-----------------|-----------------|-----------------|-------------------|
| Mercasa1  | 192.168.70.1    | 192.168.70.62   | 192.168.70.0    | 192.168.70.63     |
| Mercasa2  | 192.168.70.65   | 192.168.70.126  | 192.168.70.64   | 192.168.70.127    |
| Navantia1 | 192.168.70.129  | 192.168.70.190  | 192.168.70.128  | 192.168.70.191    |
| Navantia2 | 192.168.70.193  | 192.168.70.254  | 192.168.70.192  | 192.168.70.255    |



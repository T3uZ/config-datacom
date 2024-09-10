# config-datacom
## OSPF: Configuração

Confgurando VLAN na Interface
```
config
vlan VLAN_OSPF
  interface ten-gigabit-ethernet-1/1/1

```


Configurando VLAN OSPF
```
config
interface l3 VLAN_OSPF
  ipv4 address X.X.X.X/XX
    lower-layer-if vlan VLAN_OSPF

```

Configurar IP no loopback 
```
config
interface loopback 0
  ipv4 address X.X.X.X/XX

```

Configurando OSPF
```
config
  router ospf 1
  router-id X.X.X.X //Mesmo IP que foi colocado no loopback
  area 0
    interace l3-VLAN_OSPF //VLAN que estamos fechando para OSPF
      network-type point-to-point

    interface loopback-0

```


Comandos para analise de problemas
```
show ip ospf
show ip ospf neighbor
show ip ospf database
show ip ospf interface
show ip ospf detail
show ip ospf extensive
show ip ospf brief
show ip ospf database external
show ip route ospf
show ip rib ospf

```

MPLS LDP
```
configure
!
mpls ldp
    lsr-id loopback-0
    interface 13-VAN_OSPF
!
    neighbor targeted X.X.X.X //IP dos outros roteadores (IP do MPLS)

```

Habilitar no OSPF o envio da LSA type 10 opaque:

```
router ospf 1 vrf global
mpls-te router-id loopback-0
```

Habilitar o RSVP nas interfaces L3:

```
mpls rsvp interface l3-<INTERFACE-NAME>
```

Configuração dos caminhos:

```
mpls traffic-eng explicit-path <NAME> //Exemplo: UAE-P71-MNI-JTI
hop <1-65535> ipv4 next-address <IP ADDRESS> <LOOSE | STRICT>
```


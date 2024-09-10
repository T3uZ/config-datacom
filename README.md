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
  router-id X.X.X.X/XX //Mesmo IP que foi colocado no loopback
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

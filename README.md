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
interface loopback 0
  ipv4 address X.X.X.X/XX

```

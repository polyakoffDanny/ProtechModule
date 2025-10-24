1. Добавил маршрутизатор RTR AS 200:
![](Лабораторная%20№5.%20BGP.-21.10.2025-19_10.png)

2. Пункт 3-4. Перед настройкой BGP настроил IP адреса роутеров:
```
Piter RTR1
Router(config)#interface Ethernet0/2
Router(config-if)#ip address 10.0.12.1 255.255.255.0
Router(config-if)#no shut

RTR AS 200
Router(config)#interface Ethernet0/2
Router(config-if)#ip address 10.0.12.2 255.255.255.0
Router(config-if)#no shut
Router(config)#interface Ethernet0/1
Router(config-if)#ip address 10.0.23.2 255.255.255.0
Router(config-if)#no shut

KZN RTR1
Router(config)#interface Ethernet0/1
Router(config-if)#ip address 10.0.23.3 255.255.255.0
Router(config-if)#no shut
```

Настройка BGP:
```
Piter RTR1
Router(config)#router bgp 100
Router(config)#bgp router-id 1.1.1.1
Router(config)#neighbor 10.0.12.2 remote-as 200
Router(config)#network 172.18.71.0 mask 255.255.255.240
Router(config)#network 172.18.77.0 mask 255.255.255.240
Router(config)#network 172.18.112.0 mask 255.255.255.240

RTR AS 200
Router(config)#router bgp 200
Router(config)#bgp router-id 2.2.2.2
Router(config)#neighbor 10.0.12.1 remote-as 100
Router(config)#neighbor 10.0.23.3 remote-as 300


KZN RTR1
Router(config)#router bgp 300
Router(config)#bgp router-id 3.3.3.3
Router(config)#neighbor 10.0.23.2 remote-as 200
Router(config)#network 10.10.4.0 mask 255.255.255.0
Router(config)#network 10.10.71.0 mask 255.255.255.0
Router(config)#network 10.10.84.16 mask 255.255.255.240
Router(config)#network 10.10.86.0 mask 255.255.255.224
```

Итог:
![](Лабораторная%20№5.%20BGP.-22.10.2025-17_10.png)

![](Лабораторная%20№5.%20BGP.-22.10.2025-17_10-1.png)





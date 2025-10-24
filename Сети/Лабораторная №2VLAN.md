1. Пункты 1-3 представлены на рисунке ниже, далее включил все устройства
![|700x393](Лабораторная%20№2.%20VLAN.-19.10.2025-21_10.png)

2. Пункт 4. Присвоил VLAN на каждом порту коммутаторов доступа, который смотрит на ПК в соответствии с таблицей, ниже пример:

```
Switch(config)#int e0/0
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 4
Switch(config)#vlan 4
Switch(config-vlan)#name engineering
```

3. Пункт 5. Присвоил каждому ПК ip, ниже пример:
```
PC436_1:ip 10.10.4.2/24 10.10.4.1
PC436_2:ip 10.10.71.2/24 10.10.71.1
PC436_3:ip 10.10.84.18/28 10.10.84.17
PC436_4:ip 10.10.86.2/27 10.10.86.1
PC436_5:ip 10.10.86.3/27 10.10.86.1
```

4. Пункт 6-8,11. Разрешил прохождение трафика между коммутаторами только по используемым VLAN’ам, отключил автосогласование DTP и неиспользуемые порты, изменил native vlan на 999:

```
Switch(config)#int range e1/1
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan [нужные вланы]
Switch(config-if)#switchport trunk encapsulation dot1q
Switch(config-if)#switchport trunk native vlan 999 - измена native влана
Switch(config-if)#switchport nonegotiate - отключение DTP
Switch(config)#int range e1/2-3
Switch(config-if)#shut - отключение ненужных портов
```

5. Между Switch1_ACS и Switch3_DSTR настроил LACP в режиме Active
```
Switch(config)#int range e1/1-2
Switch(config-if-range)#channel-protocol lacp
Switch(config-if-range)#channel-group 1 mode active
Switch(config)#int port-channel 1
Switch(config-if)#switchport trunk encapsulation dot1q
Switch(config-if)#switchport mode trunk
```

6. Настроил взаимодействие между сегментом руководителей и стажёров на устройстве Switch3_DSTR:
```
Switch(config)#ip routing
Switch(config)#int vlan 84
Switch(config-if)#ip addr 10.10.84.17 255.255.255.240
Switch(config-if)#no shutdown
```

Ниже скрины подтверждения:

![|700x393](Лабораторная%20№2.%20VLAN.-20.10.2025-00_10.png)

![|700x393](Лабораторная%20№2.%20VLAN.-20.10.2025-00_10-1.png)

![|700x393](Лабораторная%20№2.%20VLAN.-20.10.2025-00_10-2.png)


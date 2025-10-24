1. Пункты 1-10. Использовались те же команды, что и ранее
2. Пункт 11. Начнем с настройки PVST в Питерском филиале, перед этим создал вланы на SW1_CORE, SW2_CORE и транки:
``` 
взято с SW2_CORE - на SW1_CORE наоборот раскинул приоритетность
Switch(config)#spanning-tree vlan 77 root primary
Switch(config)#spanning-tree vlan 112 root primary
Switch(config)#spanning-tree vlan 71 root secondary
```

Теперь настроим MSTP в Казанском офисе:
```
взято с SW2_CORE - на SW1_CORE наоборот раскинул приоритетность
Switch(config)#spanning-tree mode mst
Switch(config)#spanning-tree mst configuration
Switch(config-mst)#name kzn
Switch(config-mst)#revision 1
Switch(config-mst)#instance 1 vlan 4,71,984
Switch(config-mst)#instance 2 vlan 84,86
Switch(config)#spanning-tree mst 1 root secondary
Switch(config)#spanning-tree mst 2 root primary
```

Итог:
![|700x393](Лабораторная%20№3.%20STP.-20.10.2025-14_10.png)
![|700x393](Лабораторная%20№3.%20STP.-20.10.2025-14_10-1.png)


3. Пункт 12. На коммутаторах ядра Питера в сторону нижестоящих устройств настроить Root Guard:
``` 
Switch(config)#int range e0/1,e/3
Switch(config-if-range)#spanning-tree guard root
```

4. Пункт 13-16. Настроил терминацию необходимых вланов на определенных устройствах, то есть настроил SVI-интерфейсы и назначил им IP, пример:
``` 
Switch(config)#interface [нужный влан]
Switch(config-if)#ip addr [gateway+mask]
```
![|342x89](Лабораторная%20№3.%20STP.-20.10.2025-17_10.png)
![|323x39](Лабораторная%20№3.%20STP.-20.10.2025-17_10-1.png)
![|336x99](Лабораторная%20№3.%20STP.-20.10.2025-17_10-2.png)

Проверка: 
![|545x398](Лабораторная%20№3.%20STP.-20.10.2025-18_10.png)

![|549x420](Лабораторная%20№3.%20STP.-20.10.2025-18_10-1.png)

![|560x476](Лабораторная%20№3.%20STP.-20.10.2025-18_10-2.png)

![|547x310](Лабораторная%20№3.%20STP.-20.10.2025-18_10-3.png)

![|545x447](Лабораторная%20№3.%20STP.-20.10.2025-18_10-4.png)

![|542x456](Лабораторная%20№3.%20STP.-20.10.2025-18_10-5.png)

5. Пункт 17. На коммутаторах доступа в сторону ПК настроить PortFast и BPDU Guard:
```
Switch(config-if-range)# spanning-tree portfast
Switch(config-if-range)# spanning-tree bpduguard enable
```

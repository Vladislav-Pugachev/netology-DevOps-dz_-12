1.
> Windox:
- ipconfig
> Linux:
- ip -c -br link

2.
> Протокол LLDP

> Пакет lldpctl

3.

> Для разделения сетей на коммутаторе используется VLAN

> Для настройки VLAN в Linux используется пакет vlan

```buildoutcfg
auto vlan1400
iface vlan1400 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        vlan_raw_device eth0
```

4.

>Типы агрегации:
- balance-rr
- active-backup
- balance-xor
- 802.3ad (LACP)
- balance-tlb
- balance-alb
>Опции:
- ad_select — определяет логику выбора для агрегации по стандарту IEEE 802.3ad
- arp_interval — определяет ARP мониторинг канала
- arp_ip_target — Указывает IP адреса для ARP мониторинга
- arp_validate — Определяет будут или нет проверяться ARP запросы и ответы при использовании режима active-backup
- downdelay — Определяет время (в миллисекундах) задержки перед отключением интерфейса, если произошел сбой соединения
- fail_over_mac — Определяет как будут прописываться MAC адреса на объединенных интерфейсах в режиме active-backup при переключении интерфесов
- lacp_rate — Определяет с каким интервалом будут передаваться партнёром LACPDU пакеты в режиме 802.3ad
- max_bonds — Указывает сколько bonding устройств следует создавать драйверу
- miimon — Устанавливает периодичность MII мониторинга в миллисекундах
- num_grat_arp и num_unsol_na — Указывает количество оповещений, отправляемых соседним пирам после возникновения события отказа
- primary — указывает какой интерфейс будет первичным
- primary_reselect — Определяет как будет производиться возвращение на первичный интерфейс, после возобновления его работоспособности
- updelay — Задает время задержки в миллисекундах, перед тем как поднять линк при обнаружении восстановления канала
- use_carrier — Указывает как miimon будет определять состояние линии
- xmit_hash_policy — Определяет хэш политику передачи пакетов через объединенные интерфейсы в режиме balance-xor или 802.3ad
- resend_igmp — Указывает какое количество отчетов о принадлежности группе (IGMP membership) отсылать при возникновении события отказа
> Пример:
```buildoutcfg
auto bond0

iface bond0 inet static
    address 10.31.1.5
    netmask 255.255.255.0
    network 10.31.1.0
    gateway 10.31.1.254
    bond-slaves eth0 eth1
    bond-mode active-backup
    bond-miimon 100
    bond-downdelay 200
    bond-updelay 200

```

5.
> 6 хостов включая gateway

> 32 подсети

>
```buildoutcfg
1. Requested size: 6 hosts
Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000
Network:   10.10.10.0/29        00001010.00001010.00001010.00000 000
HostMin:   10.10.10.1           00001010.00001010.00001010.00000 001
HostMax:   10.10.10.6           00001010.00001010.00001010.00000 110
Broadcast: 10.10.10.7           00001010.00001010.00001010.00000 111
Hosts/Net: 6                     Class A, Private Internet

2. Requested size: 6 hosts
Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000
Network:   10.10.10.8/29        00001010.00001010.00001010.00001 000
HostMin:   10.10.10.9           00001010.00001010.00001010.00001 001
HostMax:   10.10.10.14          00001010.00001010.00001010.00001 110
Broadcast: 10.10.10.15          00001010.00001010.00001010.00001 111
Hosts/Net: 6                     Class A, Private Internet

3. Requested size: 6 hosts
Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000
Network:   10.10.10.16/29       00001010.00001010.00001010.00010 000
HostMin:   10.10.10.17          00001010.00001010.00001010.00010 001
HostMax:   10.10.10.22          00001010.00001010.00001010.00010 110
Broadcast: 10.10.10.23          00001010.00001010.00001010.00010 111
Hosts/Net: 6                     Class A, Private Internet
```

6.

> Адреса нужно выбрать из подсети
- 100.64.0.0/10

> С учетом необходимого колчества адресов была вырана подсети
- 100.64.0.0/26

7.
> Windows:
- arp -a просмотр arp
- arp -d * очистка всего arp
- arp -d 192.168.0.1 удаление конкретного arp

> Linux:
- arp -n  просмотр arp
- arp -d 192.168.0.1 удаление конкретного arp
- ip -s -s neigh flush all очистка всего arp
 

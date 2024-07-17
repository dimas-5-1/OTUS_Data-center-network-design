# Этап 1-7. Настройка маршрутизации между клиентскими сервисами. Настройка выхода во внешние сети для сегментов CRM, 1C

## Подготовка
### Распределение VRF RD, RT
![alt text](../../images/common/vrf-rd-rt.png)
[Оригинал схемы](../../schemes/VRF_RD-RT.drawio)

#### Стык border leafs - int-router
![alt text](../../images/POD-01/int-router.png)
[Оригинал схемы](../../schemes/Borders--Int-router.drawio)

#### Стык border leafs - ext-router
![alt text](../../images/POD-01/ext-router.png)
[Оригинал схемы](../../schemes/Borders--Ext-router.drawio)

[Идентификаторы клиентов](../Common/clients.md) 

### Параметры обмена маршрутами между сегментами
- Клиенты сегментов CRM + 1C, и клиенты сегмента CAD имеют доступ к подсетям друг друга
- Клиенты сегментов CAD и клиенты сегмента ASU имеют доступ к подсетям друг друга
- Доступ к внешним сетям имеют только клиенты сегментов CRM + 1C

### План реализации
#### Обмен внутренними маршрутами клиентов внутри ЦОД
1. С Vrf ADM, CAD, ASU маршрутизаторов border, в сторону int-router-1, посредством Route Map, экспортируются маршруты уровня адресов подсетей, без адресации /32 отдельных хостов
2. От маршрутизатора int-router-1 выполняется экспорт маршрутов в сторону маршрутизаторов border
   - Маршруты, полученные от Vrf_ADM экспортируются в Vrf_CAD
   - Маршруты, полученные от Vrf_CAD экспортируются в Vrf_ADM и Vrf_ASU
   - Маршруты, полученные от Vrf_ASU экспортируются в Vrf_CAD

#### Обмен внешними маршрутами внутри ЦОД
1. С Vrf ADM маршрутизаторов border, в сторону ext-router-1, посредством Route Map, экспортируются маршруты уровня адресов подсетей, без адресации /32 отдельных хостов
2. От маршрутизатора ext-router-1 выполняется экспорт внешних маршрутов в сторону маршрутизаторов border

## Конфигурирование
Конфигурация маршрутизаторов border-1-1/2, int-router-1, ext-router-1  приведена [здесь](../../configs/stage07_routing/POD-01/).

## Контроль применения конфигурации
### Обмен внутренними маршрутами клиентов внутри ЦОД
#### Наличие импортированных маршрутов в VRF маршрутизаторов border
##### Маршруты CAD в Vrf_ADM 
    border-1-1# show ip route vrf Vrf_ADM | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.152.1.1                Vlan110                   20/0          20:04:39

    border-1-2# show ip route vrf Vrf_ADM | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.152.2.1                Vlan120                   20/0          20:06:07

##### Маршруты ADM в Vrf_CAD 
    border-1-1# show ip route vrf Vrf_CAD | grep "10.4."
        B>*   10.4.8.0/22                  via 11.152.1.3                Vlan210                   20/0          20:08:04
        B>*   10.4.12.0/22                 via 11.152.1.3                Vlan210                   20/0          20:08:04

    border-1-2# show ip route vrf Vrf_CAD | grep "10.4."
        B>*   10.4.8.0/22                  via 11.152.2.3                Vlan220                   20/0          20:11:12
        B>*   10.4.12.0/22                 via 11.152.2.3                Vlan220                   20/0          20:11:12

##### Маршруты ASU в Vrf_CAD
    border-1-1# show ip route vrf Vrf_CAD | grep "10.8.0.0/16"
        B>*   10.8.0.0/16                  via 11.152.1.3                Vlan210                   20/0          20:14:22

    border-1-2# show ip route vrf Vrf_CAD | grep "10.8.0.0/16"
        B>*   10.8.0.0/16                  via 11.152.2.3                Vlan220                   20/0          20:15:05

##### Маршруты CAD в Vrf_ASU
    border-1-1# show ip route vrf Vrf_ASU | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.152.1.5                Vlan310                   20/0          20:17:27
    
    border-1-2# show ip route vrf Vrf_ASU | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.152.2.5                Vlan320                   20/0          20:17:47

#### Наличие импортированных маршрутов в VRF маршрутизаторов leaf
##### Маршруты CAD в Vrf_ADM 
    leaf-1-1# show ip route vrf Vrf_ADM | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.150.1.100              Vlan1000                  20/0          00:00:04

    leaf-1-3# show ip route vrf Vrf_ADM | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.150.1.100              Vlan1000                  20/0          00:01:15

##### Маршруты ADM в Vrf_CAD 
    leaf-1-1# show ip route vrf Vrf_CAD | grep "10.4."
        B>*   10.4.8.0/22                  via 11.150.1.100              Vlan2000                  20/0          00:02:58
        B>*   10.4.12.0/22                 via 11.150.1.100              Vlan2000                  20/0          00:02:58

    leaf-1-3# show ip route vrf Vrf_CAD | grep "10.4."
        B>*   10.4.8.0/22                  via 11.150.1.100              Vlan2000                  20/0          00:03:36
        B>*   10.4.12.0/22                 via 11.150.1.100              Vlan2000                  20/0          00:03:36

##### Маршруты ASU в Vrf_CAD
    leaf-1-1# show ip route vrf Vrf_CAD | grep "10.8.0.0/16"
        B>*   10.8.0.0/16                  via 11.150.1.100              Vlan2000                  20/0          00:05:11
    
    leaf-1-3# show ip route vrf Vrf_CAD | grep "10.8.0.0/16"
        B>*   10.8.0.0/16                  via 11.150.1.100              Vlan2000                  20/0          00:06:26

##### Маршруты CAD в Vrf_ASU
    leaf-1-1# show ip route vrf Vrf_ASU | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.150.1.100              Vlan3000                  20/0          00:07:08


    leaf-1-3# show ip route vrf Vrf_ASU | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.150.1.100              Vlan3000                  20/0          00:07:12

### Обмен внешними маршрутами внутри ЦОД
#### Наличие внешних маршрутов в VRF ADM маршрутизаторов border
    border-1-1# show ip route vrf Vrf_ADM | grep "200.200.0.0/16"
        B>*   200.200.0.0/16               via 11.152.1.101              Vlan910                   20/0          00:11:22

    border-1-2# show ip route vrf Vrf_ADM | grep "200.200.0.0/16"
        B>*   200.200.0.0/16               via 11.152.2.101              Vlan920                   20/0          00:11:59

#### Наличие внешних маршрутов в VRF ADM маршрутизаторов leaf
    leaf-1-1# show ip route vrf Vrf_ADM | grep "200.200.0.0/16"
        B>*   200.200.0.0/16               via 11.150.1.100              Vlan1000                  20/0          00:13:19

    leaf-1-3# show ip route vrf Vrf_ADM | grep "200.200.0.0/16"
        B>*   200.200.0.0/16               via 11.150.1.100              Vlan1000                  20/0          00:13:55

### Связность клиентов между маршрутизируемыми сегментами
#### ADM--CAD | CAD--ADM : CRM_Master -- CAD_Master

    CRM-Master# ping 10.4.24.1
        PING 10.4.24.1 (10.4.24.1) 56(84) bytes of data.
        64 bytes from 10.4.24.1: icmp_seq=1 ttl=59 time=80.3 ms
        64 bytes from 10.4.24.1: icmp_seq=2 ttl=59 time=9.27 ms
        64 bytes from 10.4.24.1: icmp_seq=3 ttl=59 time=78.4 ms
        64 bytes from 10.4.24.1: icmp_seq=4 ttl=59 time=10.1 ms

#### ASU--CAD | CAD--ASU : CAD_Master -- ASU_Slave

    CAD-Master# ping 10.8.0.2
        PING 10.8.0.2 (10.8.0.2) 56(84) bytes of data.
        64 bytes from 10.8.0.2: icmp_seq=1 ttl=59 time=12.4 ms
        64 bytes from 10.8.0.2: icmp_seq=2 ttl=59 time=7.42 ms
        64 bytes from 10.8.0.2: icmp_seq=3 ttl=59 time=8.97 ms

### Доступность выхода во внешние сети для Vrf_ADM
    CRM-Master# ping 200.200.0.1
        PING 200.200.0.1 (200.200.0.1) 56(84) bytes of data.
        64 bytes from 200.200.0.1: icmp_seq=1 ttl=62 time=37.3 ms
        64 bytes from 200.200.0.1: icmp_seq=2 ttl=62 time=5.06 ms
        64 bytes from 200.200.0.1: icmp_seq=3 ttl=62 time=3.84 ms
        64 bytes from 200.200.0.1: icmp_seq=4 ttl=62 time=6.07 ms
        64 bytes from 200.200.0.1: icmp_seq=5 ttl=62 time=4.37 ms

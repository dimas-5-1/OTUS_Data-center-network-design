# Этап 2-7. Контроль маршрутизации между клиентскими сервисами. 

Конфигурация, необходимая для обмена маршрутами между клиенскими сегментами, выполнена на [этапе 1-7](../POD-01/route_exchange.md), в POD-01.

## Обмен внутренними маршрутами клиентов внутри ЦОД
### Наличие импортированных маршрутов в VRF маршрутизаторов leaf
#### Маршруты ASU в Vrf_CAD
    leaf-2-1# show ip route vrf Vrf_CAD | grep "10.8.0.0/16"
        B>*   10.8.0.0/16                  via 11.150.1.100              Vlan2000                  20/0          04:13:01

        
    leaf-2-2# show ip route vrf Vrf_CAD | grep "10.8.0.0/16"
        B>*   10.8.0.0/16                  via 11.150.1.100              Vlan2000                  20/0          04:13:33


#### Маршруты CAD в Vrf_ASU
    leaf-2-1# show ip route vrf Vrf_ASU | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.150.1.100              Vlan3000                  20/0          04:14:42


    leaf-2-2# show ip route vrf Vrf_ASU | grep "10.4.24.0/22"
        B>*   10.4.24.0/22                 via 11.150.1.100              Vlan3000                  20/0          04:14:46


### Связность клиентов между маршрутизируемыми сегментами
#### ASU--CAD | CAD--ASU : CAD_Slave -- ASU_Master (внутри POD-02)
    CAD-Slave# ping 10.8.0.1
        PING 10.8.0.1 (10.8.0.1) 56(84) bytes of data.
        64 bytes from 10.8.0.1: icmp_seq=1 ttl=59 time=12.8 ms
        64 bytes from 10.8.0.1: icmp_seq=2 ttl=59 time=9.56 ms
        64 bytes from 10.8.0.1: icmp_seq=3 ttl=59 time=10.4 ms

#### ASU--CAD | CAD--ASU : CAD_Slave -- ASU_Slave (между POD-02 - POD-01)
    CAD-Slave# ping 10.8.0.2
        PING 10.8.0.2 (10.8.0.2) 56(84) bytes of data.
        64 bytes from 10.8.0.2: icmp_seq=1 ttl=59 time=17.7 ms
        64 bytes from 10.8.0.2: icmp_seq=2 ttl=59 time=8.58 ms
        64 bytes from 10.8.0.2: icmp_seq=3 ttl=59 time=9.39 ms


# Этап 1-5. Конфигурация клиентов

## Подготовка
Подключение клиентов отображено общей схеме топологии ЦОД, интерфейсы стыковых линков приведены [здесь](../Common/links.md).
![alt text](../../images/common/topology.png)
[Оригинал схемы](../../schemes/DC_topology.drawio)

Идентификаторы [клиентов](../Common/clients.md)

## Конфигурирование
Конфигурация оборудования клиентов приведена [здесь](../../configs/stage05_Clients/).

## Контроль применения конфигурации
Пинг Anycast Gateway адресов со стороны клиентов POD-01

### CRM_Master
    admin@CRM-Master:~$ sonic-cli
        CRM-Master# ping 10.4.11.254
        PING 10.4.11.254 (10.4.11.254) 56(84) bytes of data.
        64 bytes from 10.4.11.254: icmp_seq=1 ttl=64 time=3.07 ms
        64 bytes from 10.4.11.254: icmp_seq=2 ttl=64 time=1.43 ms
        64 bytes from 10.4.11.254: icmp_seq=3 ttl=64 time=1.60 ms

### 1C_Master
    1C-Master# ping 10.4.15.254
        PING 10.4.15.254 (10.4.15.254) 56(84) bytes of data.
        64 bytes from 10.4.15.254: icmp_seq=1 ttl=64 time=2.84 ms
        64 bytes from 10.4.15.254: icmp_seq=2 ttl=64 time=0.950 ms
        64 bytes from 10.4.15.254: icmp_seq=3 ttl=64 time=1.18 ms
        64 bytes from 10.4.15.254: icmp_seq=4 ttl=64 time=1.03 ms

### CAD_Master
    CAD-Master# ping 10.4.27.254
        PING 10.4.27.254 (10.4.27.254) 56(84) bytes of data.
        64 bytes from 10.4.27.254: icmp_seq=1 ttl=64 time=2.34 ms
        64 bytes from 10.4.27.254: icmp_seq=2 ttl=64 time=0.946 ms
        64 bytes from 10.4.27.254: icmp_seq=3 ttl=64 time=1.26 ms
        64 bytes from 10.4.27.254: icmp_seq=4 ttl=64 time=1.39 ms

### CRM_Slave
    CRM-Slave# ping 10.4.11.254
        PING 10.4.11.254 (10.4.11.254) 56(84) bytes of data.
        64 bytes from 10.4.11.254: icmp_seq=1 ttl=64 time=2.53 ms
        64 bytes from 10.4.11.254: icmp_seq=2 ttl=64 time=1.61 ms
        64 bytes from 10.4.11.254: icmp_seq=3 ttl=64 time=1.73 ms

### 1C_Slave
    1C-Slave# ping 10.4.15.254
        PING 10.4.15.254 (10.4.15.254) 56(84) bytes of data.
        64 bytes from 10.4.15.254: icmp_seq=1 ttl=64 time=3.76 ms
        64 bytes from 10.4.15.254: icmp_seq=2 ttl=64 time=1.27 ms
        64 bytes from 10.4.15.254: icmp_seq=3 ttl=64 time=1.50 ms

### ASU_Slave
    ASU-Slave# ping 10.8.255.254
        PING 10.8.255.254 (10.8.255.254) 56(84) bytes of data.
        64 bytes from 10.8.255.254: icmp_seq=1 ttl=64 time=2.56 ms
        64 bytes from 10.8.255.254: icmp_seq=2 ttl=64 time=1.01 ms
        64 bytes from 10.8.255.254: icmp_seq=3 ttl=64 time=0.969 ms

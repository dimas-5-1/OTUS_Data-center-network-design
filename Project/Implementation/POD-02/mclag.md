# Этап-2-4. Настройка резервируемых клиентских подключений (MCLAG)
## Подготовка
Подключение клиентов отображено общей схеме топологии ЦОД, интерфейсы стыковых линков приведены [здесь](../Common/links.md).
![alt text](../../images/common/topology.png)
[Оригинал схемы](../../schemes/DC_topology.drawio)

Идентификаторы [MCLAG](../Common/mclag_ids.md)


## Конфигурирование
Конфигурация маршрутизаторов leaf-2-1,2 приведена [здесь](../../configs/stage04_MCLAG/POD-02/).

## Контроль применения конфигурации
    leaf-2-1# show mclag brief
        Domain ID            : 1
        Role                 : active
        Session Status       : up
        Peer Link Status     : up
        Source Address       : 12.1.1.0
        Peer Address         : 12.1.2.0
        Peer Link            : PortChannel1
        Keepalive Interval   : 1 secs
        Session Timeout      : 30 secs
        Delay Restore        : 90 secs
        System Mac           : 50:0a:03:00:00:00
        Mclag System Mac     : 00:00:b1:b1:b1:b1
        Gateway Mac          : 00:21:00:21:00:21


        Number of MLAG Interfaces:2
        -----------------------------------------------------------
        MLAG Interface       Local/Remote Status
        -----------------------------------------------------------
        PortChannel2             up/up
        PortChannel3             up/up


    leaf-2-2# show mclag brief
        Domain ID            : 1
        Role                 : standby
        Session Status       : up
        Peer Link Status     : up
        Source Address       : 12.1.2.0
        Peer Address         : 12.1.1.0
        Peer Link            : PortChannel1
        Keepalive Interval   : 1 secs
        Session Timeout      : 30 secs
        Delay Restore        : 90 secs
        System Mac           : 50:0a:03:00:00:00
        Mclag System Mac     : 00:00:b1:b1:b1:b1
        Gateway Mac          : 00:21:00:21:00:21


        Number of MLAG Interfaces:2
        -----------------------------------------------------------
        MLAG Interface       Local/Remote Status
        -----------------------------------------------------------
        PortChannel2             up/up
        PortChannel3             up/up

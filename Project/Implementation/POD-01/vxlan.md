# Этап 1-6. Настройка VXLAN

## Подготовка
### Схема Overlay
![alt text](../../images/common/dc-overlay.png)
[Оригинал схемы](../../schemes/DC_Overlay.drawio)

Параметры [vtep интерфейсов](../Common/vxlan_addr.md)

## Конфигурирование
Конфигурация маршрутизаторов приведена [здесь](../../configs/stage06_VTEP/POD-01/).

## Контроль применения конфигурации
### VTEP интерфейсы и состояние VXLAN-туннелей
#### leaf-1-1
    leaf-1-1# show vxlan interface
        VTEP Name        :  vtep1
        VTEP Source IP   :  11.1.1.100
        EVPN NVO Name    :  nvo1
        EVPN VTEP        :  vtep1
        Source Interface :  Loopback1

    leaf-1-1# show vxlan vlanvnimap
        VLAN      VNI
        ======    =====
        Vlan1000  10000
        Vlan101   10101
        Vlan102   10201
        Vlan2000  20000
        Vlan201   20101
        Vlan3000  30000
        Vlan301   30101

    leaf-1-1# show vxlan vrfvnimap
        VRF       VNI
        ======    =====
        Vrf_ADM   10000
        Vrf_ASU   30000
        Vrf_CAD   20000


    leaf-1-1# show vxlan tunnel
        Name                SIP               DIP                 source      operstatus
        =======             ======            ======              ======      ========
        EVPN_11.1.3.100     11.1.1.100        11.1.3.100          EVPN        oper_up
        EVPN_11.150.1.100   11.1.1.100        11.150.1.100        EVPN        oper_up
        EVPN_11.150.2.101   11.1.1.100        11.150.2.101        EVPN        oper_up

#### leaf-1-2
    leaf-1-2# show vxlan interface
        VTEP Name        :  vtep1
        VTEP Source IP   :  11.1.1.100
        EVPN NVO Name    :  nvo1
        EVPN VTEP        :  vtep1
        Source Interface :  Loopback1

    leaf-1-2# show vxlan tunnel
        Name                SIP               DIP                 source      operstatus
        =======             ======            ======              ======      ========
        EVPN_11.1.3.100     11.1.1.100        11.1.3.100          EVPN        oper_up
        EVPN_11.150.1.100   11.1.1.100        11.150.1.100        EVPN        oper_up
        EVPN_11.150.2.101   11.1.1.100        11.150.2.101        EVPN        oper_up

    leaf-1-2# show vxlan vlanvnimap
        VLAN      VNI
        ======    =====
        Vlan1000  10000
        Vlan101   10101
        Vlan102   10201
        Vlan2000  20000
        Vlan201   20101
        Vlan3000  30000
        Vlan301   30101

    leaf-1-2# show vxlan vrfvnimap
        VRF       VNI
        ======    =====
        Vrf_ADM   10000
        Vrf_ASU   30000
        Vrf_CAD   20000

#### leaf-1-3
    leaf-1-3# show vxlan interface
        VTEP Name        :  vtep1
        VTEP Source IP   :  11.1.3.100
        EVPN NVO Name    :  nvo1
        EVPN VTEP        :  vtep1
        Source Interface :  Loopback1


    leaf-1-3# show vxlan tunnel
        Name                SIP               DIP                 source      operstatus
        =======             ======            ======              ======      ========
        EVPN_11.1.1.100     11.1.3.100        11.1.1.100          EVPN        oper_up
        EVPN_11.150.1.100   11.1.3.100        11.150.1.100        EVPN        oper_up
        EVPN_11.150.2.101   11.1.3.100        11.150.2.101        EVPN        oper_up



    leaf-1-3# show vxlan vlanvnimap
        VLAN      VNI
        ======    =====
        Vlan1000  10000
        Vlan101   10101
        Vlan102   10201
        Vlan2000  20000
        Vlan201   20101
        Vlan3000  30000
        Vlan301   30101


    leaf-1-3# show vxlan vrfvnimap
        VRF       VNI
        ======    =====
        Vrf_ADM   10000
        Vrf_ASU   30000
        Vrf_CAD   20000

#### leaf-1-4
    leaf-1-4# show vxlan interface
        VTEP Name        :  vtep1
        VTEP Source IP   :  11.1.3.100
        EVPN NVO Name    :  nvo1
        EVPN VTEP        :  vtep1
        Source Interface :  Loopback1


    leaf-1-4# show vxlan tunnel
        Name                SIP               DIP                 source      operstatus
        =======             ======            ======              ======      ========
        EVPN_11.1.1.100     11.1.3.100        11.1.1.100          EVPN        oper_up
        EVPN_11.150.1.100   11.1.3.100        11.150.1.100        EVPN        oper_up
        EVPN_11.150.2.101   11.1.3.100        11.150.2.101        EVPN        oper_up


    leaf-1-4# show vxlan vlanvnimap
        VLAN      VNI
        ======    =====
        Vlan1000  10000
        Vlan101   10101
        Vlan102   10201
        Vlan2000  20000
        Vlan201   20101
        Vlan3000  30000
        Vlan301   30101


    leaf-1-4# show vxlan vrfvnimap
        VRF       VNI
        ======    =====
        Vrf_ADM   10000
        Vrf_ASU   30000
        Vrf_CAD   20000

#### border-1-1
    border-1-1# show vxlan interface
        VTEP Name        :  vtep1
        VTEP Source IP   :  11.150.1.100
        EVPN NVO Name    :  nvo1
        EVPN VTEP        :  vtep1
        Source Interface :  Loopback1


    border-1-1# show vxlan tunnel
        Name                SIP               DIP                 source      operstatus
        =======             ======            ======              ======      ========
        EVPN_11.1.1.100     11.150.1.100      11.1.1.100          EVPN        oper_up
        EVPN_11.1.3.100     11.150.1.100      11.1.3.100          EVPN        oper_up
        EVPN_11.150.2.101   11.150.1.100      11.150.2.101        EVPN        oper_up

    border-1-1# show vxlan vlanvnimap
        VLAN      VNI
        ======    =====
        Vlan1000  10000
        Vlan2000  20000
        Vlan3000  30000

    border-1-1# show vxlan vrfvnimap
        VRF       VNI
        ======    =====
        Vrf_ADM   10000
        Vrf_ASU   30000
        Vrf_CAD   20000

#### border-1-2
    border-1-2# show vxlan interface
        VTEP Name        :  vtep1
        VTEP Source IP   :  11.150.2.101
        EVPN NVO Name    :  nvo1
        EVPN VTEP        :  vtep1
        Source Interface :  Loopback1


    border-1-2# show vxlan tunnel
        Name                SIP               DIP                 source      operstatus
        =======             ======            ======              ======      ========
        EVPN_11.1.1.100     11.150.2.101      11.1.1.100          EVPN        oper_up
        EVPN_11.1.3.100     11.150.2.101      11.1.3.100          EVPN        oper_up
        EVPN_11.150.1.100   11.150.2.101      11.150.1.100        EVPN        oper_up


    border-1-2# show vxlan vlanvnimap
        VLAN      VNI
        ======    =====
        Vlan1000  10000
        Vlan2000  20000
        Vlan3000  30000


    border-1-2# show vxlan vrfvnimap
        VRF       VNI
        ======    =====
        Vrf_ADM   10000
        Vrf_ASU   30000
        Vrf_CAD   20000

### Статус L2VNI
#### VNI 10101, 10201. CRM + 1C. MAC table
    leaf-1-1# show evpn mac vni 10101
        Number of MACs (local and remote) known for this VNI: 3
        MAC               Type   Intf/Remote VTEP      VLAN  Seq #'s
        50:00:00:11:11:11 local  PortChannel2          101   0/0
        50:00:00:12:12:12 remote 11.1.3.100                  0/0
        00:00:00:01:02:03 local  Vlan101               101   0/0

    leaf-1-1# show evpn mac vni 10201
        Number of MACs (local and remote) known for this VNI: 3
        MAC               Type   Intf/Remote VTEP      VLAN  Seq #'s
        50:00:00:22:22:22 remote 11.1.3.100                  0/0
        50:00:00:21:21:21 local  PortChannel3          102   0/0
        00:00:00:01:02:03 local  Vlan102               102   0/0


    leaf-1-3# show evpn mac vni 10101
        Number of MACs (local and remote) known for this VNI: 3
        MAC               Type   Intf/Remote VTEP      VLAN  Seq #'s
        50:00:00:11:11:11 remote 11.1.1.100                  0/0
        50:00:00:12:12:12 local  PortChannel2          101   0/0
        00:00:00:01:02:03 local  Vlan101               101   0/0

    leaf-1-3# show evpn mac vni 10201
        Number of MACs (local and remote) known for this VNI: 3
        MAC               Type   Intf/Remote VTEP      VLAN  Seq #'s
        50:00:00:22:22:22 local  PortChannel3          102   0/0
        50:00:00:21:21:21 remote 11.1.1.100                  0/0
        00:00:00:01:02:03 local  Vlan102               102   0/0

#### VNI 10101, 10201. CRM + 1C. Связность клиентов
##### CRM. CRM_Master--CRM_Slave
    CRM-Master# ping 10.4.8.2
        PING 10.4.8.2 (10.4.8.2) 56(84) bytes of data.
        64 bytes from 10.4.8.2: icmp_seq=1 ttl=64 time=11.9 ms
        64 bytes from 10.4.8.2: icmp_seq=2 ttl=64 time=3.67 ms
        64 bytes from 10.4.8.2: icmp_seq=3 ttl=64 time=4.28 ms

##### 1C. 1C_Master--1C_Slave
    1C-Master# ping 10.4.12.2
        PING 10.4.12.2 (10.4.12.2) 56(84) bytes of data.
        64 bytes from 10.4.12.2: icmp_seq=1 ttl=64 time=19.5 ms
        64 bytes from 10.4.12.2: icmp_seq=2 ttl=64 time=3.76 ms

### Статус L3VNI
#### L3VNI 10000, Vrf_ADM. Маршруты CRM--1C

    leaf-1-1# show ip route vrf Vrf_ADM
        Codes:  K - kernel route, C - connected, S - static, B - BGP, O - OSPF
                > - selected route, * - FIB route, q - queued route, r - rejected route, # - not installed in hardware
            Destination                  Gateway                                                 Dist/Metric   Uptime
        --------------------------------------------------------------------------------------------------------------------
        C>*   10.4.8.0/22                  Direct                        Vlan101                   0/0           19:13:07
        B>*   10.4.8.2/32                  via 11.1.3.100                Vlan1000                  20/0          06:32:02
        C>*   10.4.12.0/22                 Direct                        Vlan102                   0/0           19:13:07
        B>*   10.4.12.2/32                 via 11.1.3.100                Vlan1000                  20/0          10:27:35
        B>*   11.152.1.0/31                via 11.150.1.100              Vlan1000                  20/0          21:05:51
        B>*   11.152.1.100/31              via 11.150.1.100              Vlan1000                  20/0          21:05:51
        B>*   11.152.2.0/31                via 11.150.2.101              Vlan1000                  20/0          19:06:35
        B>*   11.152.2.100/31              via 11.150.2.101              Vlan1000                  20/0          19:06:35


        leaf-1-3# show ip route vrf Vrf_ADM
            Codes:  K - kernel route, C - connected, S - static, B - BGP, O - OSPF
                    > - selected route, * - FIB route, q - queued route, r - rejected route, # - not installed in hardware
                Destination                  Gateway                                                 Dist/Metric   Uptime
            --------------------------------------------------------------------------------------------------------------------
            C>*   10.4.8.0/22                  Direct                        Vlan101                   0/0           19:11:04
            B>*   10.4.8.1/32                  via 11.1.1.100                Vlan1000                  20/0          08:55:27
            C>*   10.4.12.0/22                 Direct                        Vlan102                   0/0           19:11:04
            B>*   10.4.12.1/32                 via 11.1.1.100                Vlan1000                  20/0          02:30:23
            B>*   11.152.1.0/31                via 11.150.1.100              Vlan1000                  20/0          21:08:19
            B>*   11.152.1.100/31              via 11.150.1.100              Vlan1000                  20/0          21:08:19
            B>*   11.152.2.0/31                via 11.150.2.101              Vlan1000                  20/0          19:09:03
            B>*   11.152.2.100/31              via 11.150.2.101              Vlan1000                  20/0          19:09:03

#### L3VNI 10000, Vrf_ADM. Связность клиентов CRM--1C
##### CRM_Master--1С_Master
    CRM-Master# ping 10.4.12.1
        PING 10.4.12.1 (10.4.12.1) 56(84) bytes of data.
        64 bytes from 10.4.12.1: icmp_seq=1 ttl=63 time=4.69 ms
        64 bytes from 10.4.12.1: icmp_seq=2 ttl=63 time=2.87 ms
        64 bytes from 10.4.12.1: icmp_seq=3 ttl=63 time=5.02 ms
        64 bytes from 10.4.12.1: icmp_seq=4 ttl=63 time=2.98 ms


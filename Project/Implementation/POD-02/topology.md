# Этап 2-1. Построение топологии, настройка адресации линков POD-01

## Подготовка
Топология POD-02 соответствует общей схеме сети ![общей схеме сети](/Project/images/common/topology.png)

Интерфейсы соединяются и конфигурируются в сооствествии со [списком линков](links.md).

## Конфигурирование
Конфигурация линков маршрутизаторов и клиентов приведена [здесь](../../configs/stage01_underlay_ipaddr/POD-02/).

## Контроль применения конфигурации
### L3 линки
##### spine-2-1

    spine-2-1# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Ethernet1            12.2.1.0/31                                       up/up
        Ethernet2            12.2.1.2/31                                       up/up
        Ethernet10           11.102.1.1/31                                     up/up
        Loopback0            12.0.1.0/32                                       up/up


    # spine-2-1 -- leaf-2-1 
        spine-2-1# ping 12.2.1.1
        PING 12.2.1.1 (12.2.1.1) 56(84) bytes of data.
        64 bytes from 12.2.1.1: icmp_seq=1 ttl=64 time=0.947 ms
        64 bytes from 12.2.1.1: icmp_seq=2 ttl=64 time=0.931 ms



    #spine-2-1 -- leaf-2-2 
        spine-2-1# ping 12.2.1.3
        PING 12.2.1.3 (12.2.1.3) 56(84) bytes of data.
        64 bytes from 12.2.1.3: icmp_seq=1 ttl=64 time=1.38 ms
        64 bytes from 12.2.1.3: icmp_seq=2 ttl=64 time=0.812 ms
  

    #spine-2-1 -- spine-1-1 
        spine-2-1# ping 11.102.1.1
        PING 11.102.1.1 (11.102.1.1) 56(84) bytes of data.
        64 bytes from 11.102.1.1: icmp_seq=1 ttl=64 time=0.111 ms
        64 bytes from 11.102.1.1: icmp_seq=2 ttl=64 time=0.055 ms
        64 bytes from 11.102.1.1: icmp_seq=3 ttl=64 time=0.040 ms



##### spine-2-2

    spine-2-2# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Ethernet1            12.2.2.0/31                                       up/up
        Ethernet2            12.2.2.2/31                                       up/up
        Ethernet10           11.102.2.1/31                                     up/up
        Loopback0            12.0.2.0/32                                       up/up


    # spine-2-2 -- leaf-2-1 
        spine-2-2# ping 12.2.2.1
        PING 12.2.2.1 (12.2.2.1) 56(84) bytes of data.
        64 bytes from 12.2.2.1: icmp_seq=1 ttl=64 time=1.35 ms
        64 bytes from 12.2.2.1: icmp_seq=2 ttl=64 time=0.721 ms
        64 bytes from 12.2.2.1: icmp_seq=3 ttl=64 time=0.801 ms



    #spine-2-2 -- leaf-2-2 
        spine-2-2# ping 12.2.2.3
        PING 12.2.2.3 (12.2.2.3) 56(84) bytes of data.
        64 bytes from 12.2.2.3: icmp_seq=1 ttl=64 time=1.51 ms
        64 bytes from 12.2.2.3: icmp_seq=2 ttl=64 time=1.48 ms
        64 bytes from 12.2.2.3: icmp_seq=3 ttl=64 time=0.639 ms



    #spine-2-2 -- spine-1-2 
        spine-2-2# ping 11.102.2.0
        PING 11.102.2.0 (11.102.2.0) 56(84) bytes of data.
        64 bytes from 11.102.2.0: icmp_seq=1 ttl=64 time=1.15 ms
        64 bytes from 11.102.2.0: icmp_seq=2 ttl=64 time=0.932 ms
        64 bytes from 11.102.2.0: icmp_seq=3 ttl=64 time=1.12 ms


### L2 линки
#### leaf-2-1
    leaf-2-1# show lldp neighbor
        -----------------------------------------------------------
        LLDP Neighbors
        -----------------------------------------------------------
        Interface:   Ethernet1,via: LLDP
        Chassis:
            ChassisID:    50:0a:01:00:00:00
            SysName:      spine-2-1
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.75
            MgmtIP:       fe80::520a:1ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet1
            PortDescr:    to_leaf-2-1
        -----------------------------------------------------------
        Interface:   Ethernet2,via: LLDP
        Chassis:
            ChassisID:    50:0a:02:00:00:00
            SysName:      spine-2-2
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.144
            MgmtIP:       fe80::520a:2ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet1
            PortDescr:    to_leaf-2-1
        -----------------------------------------------------------
        Interface:   Ethernet4,via: LLDP
        Chassis:
            ChassisID:    50:0a:04:00:00:00
            SysName:      leaf-2-2
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.140
            MgmtIP:       fe80::520a:4ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet4
            PortDescr:    leaf-2-1_portchan1_member
        -----------------------------------------------------------
        Interface:   Ethernet5,via: LLDP
        Chassis:
            ChassisID:    50:0a:04:00:00:00
            SysName:      leaf-2-2
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.140
            MgmtIP:       fe80::520a:4ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet5
            PortDescr:    leaf-2-1_portchan1_member
        -----------------------------------------------------------
        Interface:   Ethernet8,via: LLDP
        Chassis:
            ChassisID:    00:00:00:32:32:32
            SysName:      CAD-Slave
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet1
            PortDescr:    Eth1/2
        -----------------------------------------------------------
        Interface:   Ethernet9,via: LLDP
        Chassis:
            ChassisID:    00:00:00:41:41:41
            SysName:      ASU-Master
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet1
            PortDescr:    Eth1/2
        -----------------------------------------------------------


    leaf-2-1# show interface PortChannel 1
        PortChannel1 is up, line protocol is up, mode LACP
        Description: leaf-2-2_mclag_peer-link
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Fallback: Enabled, Operational
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 20.0GB
        LACP mode ACTIVE interval FAST priority 65535 address 50:0a:03:00:00:00
        Members in this channel: Ethernet4(Selected)
        LACP Actor port 5  address 50:0a:03:00:00:00 key 1
        LACP Partner port 5  address 50:0a:04:00:00:00 key 1
        Members in this channel: Ethernet5(Selected)
        LACP Actor port 6  address 50:0a:03:00:00:00 key 1
        LACP Partner port 6  address 50:0a:04:00:00:00 key 1

     
    leaf-2-1# show interface PortChannel 2
        PortChannel2 is up, line protocol is up, mode Static
        Description: CAD_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet8


    leaf-2-1# show interface PortChannel 3
        PortChannel3 is up, line protocol is up, mode Static
        Description: ASU_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet9


#### leaf-2-2

    leaf-2-2# show lldp neighbor
        -----------------------------------------------------------
        LLDP Neighbors
        -----------------------------------------------------------
        Interface:   Ethernet1,via: LLDP
        Chassis:
            ChassisID:    50:0a:01:00:00:00
            SysName:      spine-2-1
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.75
            MgmtIP:       fe80::520a:1ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet2
            PortDescr:    to_leaf-2-2
        -----------------------------------------------------------
        Interface:   Ethernet2,via: LLDP
        Chassis:
            ChassisID:    50:0a:02:00:00:00
            SysName:      spine-2-2
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.144
            MgmtIP:       fe80::520a:2ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet2
            PortDescr:    to_leaf-2-2
        -----------------------------------------------------------
        Interface:   Ethernet4,via: LLDP
        Chassis:
            ChassisID:    50:0a:03:00:00:00
            SysName:      leaf-2-1
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.39
            MgmtIP:       fe80::520a:3ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet4
            PortDescr:    leaf-2-2_portchan1_member
        -----------------------------------------------------------
        Interface:   Ethernet5,via: LLDP
        Chassis:
            ChassisID:    50:0a:03:00:00:00
            SysName:      leaf-2-1
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            MgmtIP:       10.99.83.39
            MgmtIP:       fe80::520a:3ff:fe00:0
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet5
            PortDescr:    leaf-2-2_portchan1_member
        -----------------------------------------------------------
        Interface:   Ethernet8,via: LLDP
        Chassis:
            ChassisID:    00:00:00:32:32:32
            SysName:      CAD-Slave
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet2
            PortDescr:    Eth1/3
        -----------------------------------------------------------
        Interface:   Ethernet9,via: LLDP
        Chassis:
            ChassisID:    00:00:00:41:41:41
            SysName:      ASU-Master
            SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
            TTL:          120
            Capability:   ROUTER, ON
        Port
            PortID:       Ethernet2
            PortDescr:    Eth1/3
        -----------------------------------------------------------


    leaf-2-2# show interface PortChannel 1
        PortChannel1 is up, line protocol is up, mode LACP
        Description: leaf-2-1_mclag_peer-link
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Fallback: Enabled, Operational
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 20.0GB
        LACP mode ACTIVE interval FAST priority 65535 address 50:0a:04:00:00:00
        Members in this channel: Ethernet4(Selected)
        LACP Actor port 5  address 50:0a:04:00:00:00 key 1
        LACP Partner port 5  address 50:0a:03:00:00:00 key 1
        Members in this channel: Ethernet5(Selected)
        LACP Actor port 6  address 50:0a:04:00:00:00 key 1
        LACP Partner port 6  address 50:0a:03:00:00:00 key 1

     
    leaf-2-2# show interface PortChannel 2
        PortChannel2 is up, line protocol is up, mode Static
        Description: CAD_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet8


    leaf-2-2# show interface PortChannel 3
        PortChannel3 is up, line protocol is up, mode Static
        Description: ASU_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet9


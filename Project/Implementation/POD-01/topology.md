# Этап 1-1. Построение топологии, настройка адресации линков POD-01

## Подготовка
Топология POD-01 соответствует [общей схеме сети](/Project/images/common/topology.png). Интерфейсы соединяются и конфигурируются в сооствествии со [списком линков](links.md).

## Конфигурирование
Конфигурация линков маршрутизаторов и клиентов приведена [здесь](../../configs/stage01_underlay_ipaddr/POD-01/).

## Контроль применения конфигурации
### L3 линки
##### spine-1-1

    # show ip interfaces
    Flags: U-Unnumbered interface, A-Anycast IP
    -----------------------------------------------------------------------------------------------
    Interface            IP address/mask                    VRF            Admin/Oper     Flags
    -----------------------------------------------------------------------------------------------
    Ethernet1            11.2.1.0/31                                       up/up
    Ethernet2            11.2.1.2/31                                       up/up
    Ethernet3            11.2.1.4/31                                       up/up
    Ethernet4            11.2.1.6/31                                       up/up
    Ethernet5            11.2.1.8/31                                       up/up
    Ethernet6            11.2.1.10/31                                      up/up
    Ethernet10           11.102.1.0/31                                     up/up
    Loopback0            11.0.1.0/32                                       up/up

    # spine-1-1 -- leaf-1-1 
        spine-1-1# ping 11.2.1.1
        PING 11.2.1.1 (11.2.1.1) 56(84) bytes of data.
        64 bytes from 11.2.1.1: icmp_seq=1 ttl=64 time=1.23 ms
        64 bytes from 11.2.1.1: icmp_seq=2 ttl=64 time=0.755 ms
        64 bytes from 11.2.1.1: icmp_seq=3 ttl=64 time=1.02 ms
        64 bytes from 11.2.1.1: icmp_seq=4 ttl=64 time=0.730 ms


    #spine-1-1 -- leaf-1-2 
        spine-1-1# ping 11.2.1.3
        PING 11.2.1.3 (11.2.1.3) 56(84) bytes of data.
        64 bytes from 11.2.1.3: icmp_seq=1 ttl=64 time=0.742 ms
        64 bytes from 11.2.1.3: icmp_seq=2 ttl=64 time=0.726 ms
        64 bytes from 11.2.1.3: icmp_seq=3 ttl=64 time=0.700 ms
  

    #spine-1-1 -- leaf-1-3 
        spine-1-1# ping 11.2.1.5
        PING 11.2.1.5 (11.2.1.5) 56(84) bytes of data.
        64 bytes from 11.2.1.5: icmp_seq=1 ttl=64 time=1.48 ms
        64 bytes from 11.2.1.5: icmp_seq=2 ttl=64 time=0.988 ms
        64 bytes from 11.2.1.5: icmp_seq=3 ttl=64 time=0.979 ms
        64 bytes from 11.2.1.5: icmp_seq=4 ttl=64 time=1.23 ms
      
    #spine-1-1 -- leaf-1-4 
        spine-1-1# ping 11.2.1.7
        PING 11.2.1.7 (11.2.1.7) 56(84) bytes of data.
        64 bytes from 11.2.1.7: icmp_seq=1 ttl=64 time=2.20 ms
        64 bytes from 11.2.1.7: icmp_seq=2 ttl=64 time=0.943 ms
        64 bytes from 11.2.1.7: icmp_seq=3 ttl=64 time=1.36 ms


    #spine-1-1 -- border-1-1 
        spine-1-1# ping 11.2.1.9
        PING 11.2.1.9 (11.2.1.9) 56(84) bytes of data.
        64 bytes from 11.2.1.9: icmp_seq=1 ttl=64 time=1.22 ms
        64 bytes from 11.2.1.9: icmp_seq=2 ttl=64 time=1.21 ms
        64 bytes from 11.2.1.9: icmp_seq=3 ttl=64 time=1.05 ms


    #spine-1-1 -- border-1-2 
        spine-1-1# ping 11.2.1.11
        PING 11.2.1.11 (11.2.1.11) 56(84) bytes of data.
        64 bytes from 11.2.1.11: icmp_seq=1 ttl=64 time=51.0 ms
        64 bytes from 11.2.1.11: icmp_seq=2 ttl=64 time=1.16 ms


##### spine-1-2

    # show ip interfaces
    Flags: U-Unnumbered interface, A-Anycast IP
    -----------------------------------------------------------------------------------------------
    Interface            IP address/mask                    VRF            Admin/Oper     Flags
    -----------------------------------------------------------------------------------------------
    Ethernet1            11.2.2.0/31                                       up/up
    Ethernet2            11.2.2.2/31                                       up/up
    Ethernet3            11.2.2.4/31                                       up/up
    Ethernet4            11.2.2.6/31                                       up/up
    Ethernet5            11.2.2.8/31                                       up/up
    Ethernet6            11.2.2.10/31                                      up/up
    Ethernet10           11.102.2.0/31                                     up/up
    Loopback0            11.0.2.0/32                                       up/up

    # spine-1-2 -- leaf-1-1 
        spine-1-2# ping 11.2.2.1
        PING 11.2.2.1 (11.2.2.1) 56(84) bytes of data.
        64 bytes from 11.2.2.1: icmp_seq=1 ttl=64 time=1.72 ms
        64 bytes from 11.2.2.1: icmp_seq=2 ttl=64 time=0.720 ms
        64 bytes from 11.2.2.1: icmp_seq=3 ttl=64 time=0.991 ms


    #spine-1-2 -- leaf-1-2 
        spine-1-2# ping 11.2.2.3
        PING 11.2.2.3 (11.2.2.3) 56(84) bytes of data.
        64 bytes from 11.2.2.3: icmp_seq=1 ttl=64 time=0.893 ms
        64 bytes from 11.2.2.3: icmp_seq=2 ttl=64 time=0.887 ms
        64 bytes from 11.2.2.3: icmp_seq=3 ttl=64 time=0.495 ms


    #spine-1-2 -- leaf-1-3 
        spine-1-2# ping 11.2.2.5
        PING 11.2.2.5 (11.2.2.5) 56(84) bytes of data.
        64 bytes from 11.2.2.5: icmp_seq=1 ttl=64 time=1.24 ms
        64 bytes from 11.2.2.5: icmp_seq=2 ttl=64 time=0.639 ms
        64 bytes from 11.2.2.5: icmp_seq=3 ttl=64 time=0.865 ms

      
    #spine-1-2 -- leaf-1-4 
        spine-1-2# ping 11.2.2.7
        PING 11.2.2.7 (11.2.2.7) 56(84) bytes of data.
        64 bytes from 11.2.2.7: icmp_seq=1 ttl=64 time=0.919 ms
        64 bytes from 11.2.2.7: icmp_seq=2 ttl=64 time=2.07 ms
        64 bytes from 11.2.2.7: icmp_seq=3 ttl=64 time=0.747 ms


    #spine-1-2 -- border-1-1 
        spine-1-2# ping 11.2.2.9
        PING 11.2.2.9 (11.2.2.9) 56(84) bytes of data.
        64 bytes from 11.2.2.9: icmp_seq=1 ttl=64 time=1.68 ms
        64 bytes from 11.2.2.9: icmp_seq=2 ttl=64 time=1.26 ms
        64 bytes from 11.2.2.9: icmp_seq=3 ttl=64 time=1.44 ms
 

    #spine-1-2 -- border-1-2 
        spine-1-2# ping 11.2.2.11
        PING 11.2.2.11 (11.2.2.11) 56(84) bytes of data.
        64 bytes from 11.2.2.11: icmp_seq=1 ttl=64 time=1.12 ms
        64 bytes from 11.2.2.11: icmp_seq=2 ttl=64 time=4.05 ms
        64 bytes from 11.2.2.11: icmp_seq=3 ttl=64 time=4.97 ms


### L2 линки
#### leaf-1-1

    show lldp neighbors
      leaf-1-1# show lldp neighbor
      -----------------------------------------------------------
      LLDP Neighbors
      -----------------------------------------------------------
      Interface:   Ethernet1,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:01:00:00
          SysName:      spine-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.235
          MgmtIP:       fe80::520a:ff:fe01:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    to_leaf-1-1
      -----------------------------------------------------------
      Interface:   Ethernet2,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:03:00:00
          SysName:      spine-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.230
          MgmtIP:       fe80::520a:ff:fe03:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    to_leaf-1-1
      -----------------------------------------------------------
      Interface:   Ethernet4,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:04:00:00
          SysName:      leaf-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.66
          MgmtIP:       fe80::520a:ff:fe04:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet4
          PortDescr:    leaf-1-1_portchan1_member
      -----------------------------------------------------------
      Interface:   Ethernet5,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:04:00:00
          SysName:      leaf-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.66
          MgmtIP:       fe80::520a:ff:fe04:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet5
          PortDescr:    leaf-1-1_portchan1_member
      -----------------------------------------------------------
      Interface:   Ethernet8,via: LLDP
        Chassis:
          ChassisID:    00:00:00:11:11:11
          SysName:      CRM-Master
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    Eth1/2
      -----------------------------------------------------------
      Interface:   Ethernet9,via: LLDP
        Chassis:
          ChassisID:    00:00:00:21:21:21
          SysName:      1C-Master
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    Eth1/2
      -----------------------------------------------------------
      Interface:   Ethernet10,via: LLDP
        Chassis:
          ChassisID:    00:00:00:31:31:31
          SysName:      CAD-Master
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    Eth1/2
      -----------------------------------------------------------

      leaf-1-1# show interface PortChannel 1
        PortChannel1 is up, line protocol is up, mode LACP
        Description: leaf-1-2_mclag_peer-link
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Fallback: Enabled, Operational
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 20.0GB
        LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:02:00:00
        Members in this channel: Ethernet4(Selected)
        LACP Actor port 5  address 50:0a:00:02:00:00 key 1
        LACP Partner port 5  address 50:0a:00:04:00:00 key 1
        Members in this channel: Ethernet5(Selected)
        LACP Actor port 6  address 50:0a:00:02:00:00 key 1
        LACP Partner port 6  address 50:0a:00:04:00:00 key 1
     
      leaf-1-1# show interface PortChannel 2
        PortChannel2 is up, line protocol is up, mode Static
        Description: CRM_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet8

      leaf-1-1# show interface PortChannel 3
        PortChannel3 is up, line protocol is up, mode Static
        Description: 1C_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet9

      leaf-1-1# show interface PortChannel 4
        PortChannel4 is up, line protocol is up, mode Static
        Description: CAD_mclag_portchan
        Minimum number of links to bring PortChannel up is 1
        Mode of IPV4 address assignment: not-set
        Mode of IPV6 address assignment: not-set
        Graceful shutdown: Disabled
        MTU 9000
        LineSpeed 1.0GB
        Members in this channel: Ethernet10


#### leaf-1-2

    leaf-1-2# show lldp neighbor
      -----------------------------------------------------------
      LLDP Neighbors
      -----------------------------------------------------------
      Interface:   Ethernet1,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:01:00:00
          SysName:      spine-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.235
          MgmtIP:       fe80::520a:ff:fe01:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    to_leaf-1-2
      -----------------------------------------------------------
      Interface:   Ethernet2,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:03:00:00
          SysName:      spine-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.230
          MgmtIP:       fe80::520a:ff:fe03:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    to_leaf-1-2
      -----------------------------------------------------------
      Interface:   Ethernet4,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:02:00:00
          SysName:      leaf-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.168
          MgmtIP:       fe80::520a:ff:fe02:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet4
          PortDescr:    leaf-1-2_portchan1_member
      -----------------------------------------------------------
      Interface:   Ethernet5,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:02:00:00
          SysName:      leaf-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.168
          MgmtIP:       fe80::520a:ff:fe02:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet5
          PortDescr:    leaf-1-2_portchan1_member
      -----------------------------------------------------------
      Interface:   Ethernet8,via: LLDP
        Chassis:
          ChassisID:    00:00:00:11:11:11
          SysName:      CRM-Master
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    Eth1/3
      -----------------------------------------------------------
      Interface:   Ethernet9,via: LLDP
        Chassis:
          ChassisID:    00:00:00:21:21:21
          SysName:      1C-Master
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    Eth1/3
      -----------------------------------------------------------
      Interface:   Ethernet10,via: LLDP
        Chassis:
          ChassisID:    00:00:00:31:31:31
          SysName:      CAD-Master
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    Eth1/3
      -----------------------------------------------------------


    leaf-1-2# show interface PortChannel 1
      PortChannel1 is up, line protocol is up, mode LACP
      Description: leaf-1-1_mclag_peer-link
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 20.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:04:00:00
      Members in this channel: Ethernet4(Selected)
      LACP Actor port 5  address 50:0a:00:04:00:00 key 1
      LACP Partner port 5  address 50:0a:00:02:00:00 key 1
      Members in this channel: Ethernet5(Selected)
      LACP Actor port 6  address 50:0a:00:04:00:00 key 1
      LACP Partner port 6  address 50:0a:00:02:00:00 key 1
     
    leaf-1-2# show interface PortChannel 2
      PortChannel2 is up, line protocol is up, mode Static
      Description: CRM_mclag_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 1.0GB
      Members in this channel: Ethernet8

    leaf-1-2# show interface PortChannel 3
      PortChannel3 is up, line protocol is up, mode Static
      Description: 1C_mclag_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 1.0GB
      Members in this channel: Ethernet9

    leaf-1-2# show interface PortChannel 4
      PortChannel4 is up, line protocol is up, mode Static
      Description: CAD_mclag_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 1.0GB
      Members in this channel: Ethernet10
  

#### border-1-1

    border-1-1# show lldp neighbor
      -----------------------------------------------------------
      LLDP Neighbors
      -----------------------------------------------------------
      Interface:   Ethernet1,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:01:00:00
          SysName:      spine-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.235
          MgmtIP:       fe80::520a:ff:fe01:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet5
          PortDescr:    to_border-1-1
      -----------------------------------------------------------
      Interface:   Ethernet2,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:03:00:00
          SysName:      spine-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.230
          MgmtIP:       fe80::520a:ff:fe03:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet5
          PortDescr:    to_border-1-1
      -----------------------------------------------------------
      Interface:   Ethernet8,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:09:00:00
          SysName:      int-router-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.83
          MgmtIP:       fe80::520a:ff:fe09:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    border-1-1_portchan_member
      -----------------------------------------------------------
      Interface:   Ethernet9,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:0a:00:00
          SysName:      ext-router-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.170
          MgmtIP:       fe80::520a:ff:fe0a:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet1
          PortDescr:    border-1-1_portchan_member
      -----------------------------------------------------------
  
    border-1-1# show interface PortChannel 2
      PortChannel2 is up, line protocol is up, mode LACP
      Description: INT-router-1_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:07:00:00
      Members in this channel: Ethernet8(Selected)
      LACP Actor port 9  address 50:0a:00:07:00:00 key 2
      LACP Partner port 2  address 50:0a:00:09:00:00 key 1

    border-1-1# show interface PortChannel 3
      PortChannel3 is up, line protocol is up, mode LACP
      Description: EXT-router-1_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:07:00:00
      Members in this channel: Ethernet9(Selected)
      LACP Actor port 10  address 50:0a:00:07:00:00 key 3
      LACP Partner port 2  address 50:0a:00:0a:00:00 key 1


#### border-1-2

    border-1-2# show lldp neighbor
      -----------------------------------------------------------
      LLDP Neighbors
      -----------------------------------------------------------
      Interface:   Ethernet1,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:01:00:00
          SysName:      spine-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.235
          MgmtIP:       fe80::520a:ff:fe01:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet6
          PortDescr:    to_border-1-1
      -----------------------------------------------------------
      Interface:   Ethernet2,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:03:00:00
          SysName:      spine-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.230
          MgmtIP:       fe80::520a:ff:fe03:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet6
          PortDescr:    to_border-1-1
      -----------------------------------------------------------
      Interface:   Ethernet8,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:09:00:00
          SysName:      int-router-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.83
          MgmtIP:       fe80::520a:ff:fe09:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    border-1-2_portchan_member
      -----------------------------------------------------------
      Interface:   Ethernet9,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:0a:00:00
          SysName:      ext-router-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.170
          MgmtIP:       fe80::520a:ff:fe0a:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet2
          PortDescr:    border-1-2_portchan_member
      -----------------------------------------------------------

    border-1-2# show interface PortChannel 2
      PortChannel2 is up, line protocol is up, mode LACP
      Description: INT-router-1_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:08:00:00
      Members in this channel: Ethernet8(Selected)
      LACP Actor port 9  address 50:0a:00:08:00:00 key 2
      LACP Partner port 3  address 50:0a:00:09:00:00 key 2

    border-1-2# show interface PortChannel 3
      PortChannel3 is up, line protocol is up, mode LACP
      Description: EXT-router-1_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:08:00:00
      Members in this channel: Ethernet9(Selected)
      LACP Actor port 10  address 50:0a:00:08:00:00 key 3
      LACP Partner port 3  address 50:0a:00:0a:00:00 key 2

#### INT-router-1

    int-router-1# show lldp neighbor
      -----------------------------------------------------------
      LLDP Neighbors
      -----------------------------------------------------------
      Interface:   Ethernet1,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:07:00:00
          SysName:      border-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.81
          MgmtIP:       fe80::520a:ff:fe07:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet8
          PortDescr:    INT-router-1_portchan_member
      -----------------------------------------------------------
      Interface:   Ethernet2,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:08:00:00
          SysName:      border-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.82
          MgmtIP:       fe80::520a:ff:fe08:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet8
          PortDescr:    INT-router-1_portchan_member
      -----------------------------------------------------------

    int-router-1# show interface PortChannel 1
      PortChannel1 is up, line protocol is up, mode LACP
      Description: border-1-1_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:09:00:00
      Members in this channel: Ethernet1(Selected)
      LACP Actor port 2  address 50:0a:00:09:00:00 key 1
      LACP Partner port 9  address 50:0a:00:07:00:00 key 2

    int-router-1# show interface PortChannel 2
      PortChannel2 is up, line protocol is up, mode LACP
      Description: border-1-2_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:09:00:00
      Members in this channel: Ethernet2(Selected)
      LACP Actor port 3  address 50:0a:00:09:00:00 key 2
      LACP Partner port 9  address 50:0a:00:08:00:00 key 2

#### EXT-router-1

    ext-router-1# show lldp neighbor
      -----------------------------------------------------------
      LLDP Neighbors
      -----------------------------------------------------------
      Interface:   Ethernet1,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:07:00:00
          SysName:      border-1-1
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.81
          MgmtIP:       fe80::520a:ff:fe07:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet9
          PortDescr:    EXT-router-1_portchan_member
      -----------------------------------------------------------
      Interface:   Ethernet2,via: LLDP
        Chassis:
          ChassisID:    50:0a:00:08:00:00
          SysName:      border-1-2
          SysDescr:     SONiC Software Version: SONiC.3.4.0-Enterprise_Base - HwSku: DellEMC-S5248f-P-25G-DPB - Distribution: Debian 9.13 - Kernel: 4.9.0-11-2-amd64
          TTL:          120
          MgmtIP:       10.99.83.82
          MgmtIP:       fe80::520a:ff:fe08:0
          Capability:   ROUTER, ON
        Port
          PortID:       Ethernet9
          PortDescr:    EXT-router-1_portchan_member
      -----------------------------------------------------------

    ext-router-1# show interface PortChannel 1
      PortChannel1 is up, line protocol is up, mode LACP
      Description: border-1-1_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:0a:00:00
      Members in this channel: Ethernet1(Selected)
      LACP Actor port 2  address 50:0a:00:0a:00:00 key 1
      LACP Partner port 10  address 50:0a:00:07:00:00 key 3


    ext-router-1# show interface PortChannel 2
      PortChannel2 is up, line protocol is up, mode LACP
      Description: border-1-2_portchan
      Minimum number of links to bring PortChannel up is 1
      Mode of IPV4 address assignment: not-set
      Mode of IPV6 address assignment: not-set
      Fallback: Enabled, Operational
      Graceful shutdown: Disabled
      MTU 9000
      LineSpeed 10.0GB
      LACP mode ACTIVE interval FAST priority 65535 address 50:0a:00:0a:00:00
      Members in this channel: Ethernet2(Selected)
      LACP Actor port 3  address 50:0a:00:0a:00:00 key 2
      LACP Partner port 10  address 50:0a:00:08:00:00 key 3


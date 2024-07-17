# Этап 1-2. Настройка VRF, и их L2 / L3 интерфейсов

## Подготовка
Vlan интерфейсы [клиентов](../Common/clients.md), размещённых в [POD-01](../../schemes/DC_Overlay.drawio) - приведены [здесь](../Common/l3_iface_addr.md)

## Конфигурирование
Конфигурация маршрутизаторов приведена [здесь](../../configs/stage02_VRFs_VLANs/POD-01/).


## Контроль применения конфигурации

### leaf-1-1
    leaf-1-1# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan101              10.4.11.254/22                     Vrf_ADM        up/up      A
        Vlan102              10.4.15.254/22                     Vrf_ADM        up/up      A
        Vlan201              10.4.27.254/22                     Vrf_CAD        up/up      A
        Vlan301              10.8.255.254/16                    Vrf_ASU        up/up      A


    leaf-1-1# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ADM             Vlan101
                            Vlan102
                            Vlan1000
        Vrf_ASU             Vlan301
                            Vlan3000
        Vrf_CAD             Vlan201
                            Vlan2000

### leaf-1-2
    leaf-1-2# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan101              10.4.11.254/22                     Vrf_ADM        up/up      A
        Vlan102              10.4.15.254/22                     Vrf_ADM        up/up      A
        Vlan201              10.4.27.254/22                     Vrf_CAD        up/up      A
        Vlan301              10.8.255.254/16                    Vrf_ASU        up/up      A


    leaf-1-2# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ADM             Vlan101
                            Vlan102
                            Vlan1000
        Vrf_ASU             Vlan301
                            Vlan3000
        Vrf_CAD             Vlan201
                            Vlan2000


### leaf-1-3
    leaf-1-3# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan101              10.4.11.254/22                     Vrf_ADM        up/up      A
        Vlan102              10.4.15.254/22                     Vrf_ADM        up/up      A
        Vlan201              10.4.27.254/22                     Vrf_CAD        up/up      A
        Vlan301              10.8.255.254/16                    Vrf_ASU        up/up      A
    
    
    leaf-1-1# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ADM             Vlan101
                            Vlan102
                            Vlan1000
        Vrf_ASU             Vlan301
                            Vlan3000
        Vrf_CAD             Vlan201
                            Vlan2000

### leaf-1-4
    leaf-1-4# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan101              10.4.11.254/22                     Vrf_ADM        up/up      A
        Vlan102              10.4.15.254/22                     Vrf_ADM        up/up      A
        Vlan201              10.4.27.254/22                     Vrf_CAD        up/up      A
        Vlan301              10.8.255.254/16                    Vrf_ASU        up/up      A


    leaf-1-4# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ADM             Vlan101
                            Vlan102
                            Vlan1000
        Vrf_ASU             Vlan301
                            Vlan3000
        Vrf_CAD             Vlan201
                            Vlan2000

### border-1-1
    border-1-1# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan110              11.152.1.0/31                      Vrf_ADM        up/up
        Vlan210              11.152.1.2/31                      Vrf_CAD        up/up
        Vlan310              11.152.1.4/31                      Vrf_ASU        up/up
        Vlan910              11.152.1.100/31                    Vrf_ADM        up/up


    border-1-1# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ADM             Vlan110
                            Vlan910
                            Vlan1000
        Vrf_ASU             Vlan310
                            Vlan3000
        Vrf_CAD             Vlan210
                            Vlan2000

### border-1-2
    border-1-2# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan120              11.152.2.0/31                      Vrf_ADM        up/up
        Vlan220              11.152.2.2/31                      Vrf_CAD        up/up
        Vlan320              11.152.2.4/31                      Vrf_ASU        up/up
    Vlan920              11.152.2.100/31                    Vrf_ADM        up/up

    border-1-2# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ADM             Vlan120
                            Vlan920
                            Vlan1000
        Vrf_ASU             Vlan320
                            Vlan3000
        Vrf_CAD             Vlan220
                            Vlan2000

### INT-router-1
    int-router-1# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan110              11.152.1.1/31                      Vrf_INT        up/up
        Vlan120              11.152.2.1/31                      Vrf_INT        up/up
        Vlan210              11.152.1.3/31                      Vrf_INT        up/up
        Vlan220              11.152.2.3/31                      Vrf_INT        up/up
        Vlan310              11.152.1.5/31                      Vrf_INT        up/up
        Vlan320              11.152.2.5/31                      Vrf_INT        up/up

### EXT-router-1
    ext-router-1# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Ethernet0            200.200.0.1/16                     Vrf_EXT        up/down
        Loopback1            100.100.100.1/32                   Vrf_EXT        up/up
        Vlan910              11.152.1.101/31                    Vrf_ADM        up/up
        Vlan920              11.152.2.101/31                    Vrf_ADM        up/up

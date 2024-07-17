# Этап 2-2. Настройка VRF, и их L2 / L3 интерфейсов

## Подготовка
Vlan интерфейсы [клиентов](../Common/clients.md), размещённых в [POD-02](../../schemes/DC_Overlay.drawio) - приведены [здесь](../Common/l3_iface_addr.md)

## Конфигурирование
Конфигурация маршрутизаторов приведена [здесь](../../configs/stage02_VRFs_VLANs/POD-02/).


## Контроль применения конфигурации

### leaf-2-1
    leaf-2-1# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan201              10.4.27.254/22                     Vrf_CAD        up/up      A
        Vlan301              10.8.255.254/16                    Vrf_ASU        up/up      A


    leaf-2-1# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ASU             Vlan301
                            Vlan3000
        Vrf_CAD             Vlan201
                            Vlan2000


### leaf-2-2
    leaf-2-2# show ip interfaces
        Flags: U-Unnumbered interface, A-Anycast IP
        -----------------------------------------------------------------------------------------------
        Interface            IP address/mask                    VRF            Admin/Oper     Flags
        -----------------------------------------------------------------------------------------------
        Vlan201              10.4.27.254/22                     Vrf_CAD        up/up      A
        Vlan301              10.8.255.254/16                    Vrf_ASU        up/up      A


    leaf-2-2# show ip vrf
        VRF-NAME            INTERFACES
        ----------------------------------------------------------------
        Vrf_ASU             Vlan301
                            Vlan3000
        Vrf_CAD             Vlan201
                            Vlan2000

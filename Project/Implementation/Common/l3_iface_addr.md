## Адресация L3 интерфейсов
---
|N|	POD|	Node|	interface|	BW|	L3_addr_A|	is anycast L3 address|	Descr|	VRF|	Parent interface|
|--|--|--|--|--|--|--|--|--|--|
|1|	1|	spine-1-1|	Loopback0|	|	11.0.1.0/32|	|	router_id|	|	|
|2|	1|	spine-1-1|	Ethernet1|	25G|	11.2.1.0/31|	|	to_leaf-1-1|	|	|
|3|	1|	spine-1-1|	Ethernet2|	25G|	11.2.1.2/31|	|	to_leaf-1-2|	|	|
|4|	1|	spine-1-1|	Ethernet3|	25G|	11.2.1.4/31|	|	to_leaf-1-3|	|	|
|5|	1|	spine-1-1|	Ethernet4|	25G|	11.2.1.6/31|	|	to_leaf-1-4|	|	|
|6|	1|	spine-1-1|	Ethernet5|	25G|	11.2.1.8/31|	|	to_border-1-1|	|	|
|7|	1|	spine-1-1|	Ethernet6|	25G|	11.2.1.10/31|	|	to_border-1-2|	|	|
|8|	1|	spine-1-1|	Ethernet10|	25G|	11.102.1.0/31|	|	to_spine-2-1|	|	|
|9|	1|	spine-1-2|	Loopback0|	|	11.0.2.0/32|	|	router_id|	|	|
|10|	1|	spine-1-2|	Ethernet1|	25G|	11.2.2.0/31|	|	to_leaf-1-1|	|	|
|11|	1|	spine-1-2|	Ethernet2|	25G|	11.2.2.2/31|	|	to_leaf-1-2|	|	|
|12|	1|	spine-1-2|	Ethernet3|	25G|	11.2.2.4/31|	|	to_leaf-1-3|	|	|
|13|	1|	spine-1-2|	Ethernet4|	25G|	11.2.2.6/31|	|	to_leaf-1-4|	|	|
|14|	1|	spine-1-2|	Ethernet5|	25G|	11.2.2.8/31|	|	to_border-1-1|	|	|
|15|	1|	spine-1-2|	Ethernet6|	25G|	11.2.2.10/31|	|	to_border-1-2|	|	|
|16|	1|	spine-1-2|	Ethernet10|	25G|	11.102.2.0/31|	|	to_spine-2-2|	|	|
|17|	1|	leaf-1-1|	Loopback0|	|	11.1.1.0/32|	|	router_id|	|	|
|18|	1|	leaf-1-1|	Loopback1|	|	11.1.1.100/32|	|	vtep|	|	|
|19|	1|	leaf-1-1|	Ethernet1|	25G|	11.2.1.1/31|	|	to_spine-1-1|	|	|
|20|	1|	leaf-1-1|	Ethernet2|	25G|	11.2.2.1/31|	|	to_spine-1-2|	|	|
|21|	1|	leaf-1-1|	Vlan101|	|	10.4.11.254/22|	1|	crm_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel2|
|22|	1|	leaf-1-1|	Vlan102|	|	10.4.15.254/22|	1|	1c_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel3|
|23|	1|	leaf-1-1|	Vlan201|	|	10.4.27.254/22|	1|	cad_access_vlan|	Vrf_CAD|	PortChannel1, PortChannel4|
|24|	1|	leaf-1-1|	Vlan301|	|	10.8.255.254/16|	1|	asu_access_vlan|	Vrf_ASU|	PortChannel1|
|25|	1|	leaf-1-2|	Loopback0|	|	11.1.2.0/32|	|	router_id|	|	|
|26|	1|	leaf-1-2|	Loopback1|	|	11.1.1.100/32|	|	vtep|	|	|
|27|	1|	leaf-1-2|	Ethernet1|	25G|	11.2.1.3/31|	|	to_spine-1-1|	|	|
|28|	1|	leaf-1-2|	Ethernet2|	25G|	11.2.2.3/31|	|	to_spine-1-2|	|	|
|29|	1|	leaf-1-2|	Vlan101|	|	10.4.11.254/22|	1|	crm_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel2|
|30|	1|	leaf-1-2|	Vlan102|	|	10.4.15.254/22|	1|	1c_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel3|
|31|	1|	leaf-1-2|	Vlan201|	|	10.4.27.254/22|	1|	cad_access_vlan|	Vrf_CAD|	PortChannel1, PortChannel4|
|32|	1|	leaf-1-2|	Vlan301|	|	10.8.255.254/16|	1|	asu_access_vlan|	Vrf_ASU|	PortChannel1|
|33|	1|	leaf-1-3|	Loopback0|	|	11.1.3.0/32|	|	router_id|	|	|
|34|	1|	leaf-1-3|	Loopback1|	|	11.1.3.100/32|	|	vtep|	|	|
|35|	1|	leaf-1-3|	Ethernet1|	25G|	11.2.1.5/31|	|	to_spine-1-1|	|	|
|36|	1|	leaf-1-3|	Ethernet2|	25G|	11.2.2.5/31|	|	to_spine-1-2|	|	|
|37|	1|	leaf-1-3|	Vlan101|	|	10.4.11.254/22|	1|	crm_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel2|
|38|	1|	leaf-1-3|	Vlan102|	|	10.4.15.254/22|	1|	1c_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel3|
|39|	1|	leaf-1-3|	Vlan201|	|	10.4.27.254/22|	1|	cad_access_vlan|	Vrf_CAD|	PortChannel1|
|40|	1|	leaf-1-3|	Vlan301|	|	10.8.255.254/16|	1|	asu_access_vlan|	Vrf_ASU|	PortChannel1, PortChannel4|
|41|	1|	leaf-1-4|	Loopback0|	|	11.1.4.0/32|	|	router_id|	|	|
|42|	1|	leaf-1-4|	Loopback1|	|	11.1.3.100/32|	|	vtep|	|	|
|43|	1|	leaf-1-4|	Ethernet1|	25G|	11.2.1.7/31|	|	to_spine-1-1|	|	|
|44|	1|	leaf-1-4|	Ethernet2|	25G|	11.2.2.7/31|	|	to_spine-1-2|	|	|
|45|	1|	leaf-1-4|	Vlan101|	|	10.4.11.254/22|	1|	crm_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel2|
|46|	1|	leaf-1-4|	Vlan102|	|	10.4.15.254/22|	1|	1c_access_vlan|	Vrf_ADM|	PortChannel1, PortChannel3|
|47|	1|	leaf-1-4|	Vlan201|	|	10.4.27.254/22|	1|	cad_access_vlan|	Vrf_CAD|	PortChannel1|
|48|	1|	leaf-1-4|	Vlan301|	|	10.5.255.254/16|	1|	asu_access_vlan|	Vrf_ASU|	PortChannel1, PortChannel4|
|49|	1|	border-1-1|	Loopback0|	|	11.150.1.0/32|	|	router_id|	|	|
|50|	1|	border-1-1|	Loopback1|	|	11.150.1.100/32|	|	vtep|	|	|
|51|	1|	border-1-1|	Ethernet1|	25G|	11.2.1.9/31|	|	to_spine-1-1|	|	|
|52|	1|	border-1-1|	Ethernet2|	25G|	11.2.2.9/31|	|	to_spine-1-2|	|	|
|53|	1|	border-1-1|	Vlan110|	|	11.152.1.0/31|	|	to_INT_router_vrf_ADM|	Vrf_ADM|	PortChannel2|
|54|	1|	border-1-1|	Vlan210|	|	11.152.1.2/31|	|	to_INT_router_vrf_CAD|	Vrf_CAD|	PortChannel2|
|55|	1|	border-1-1|	Vlan310|	|	11.152.1.4/31|	|	to_INT_router_vrf_ASU|	Vrf_ASU|	PortChannel2|
|56|	1|	border-1-1|	Vlan910|	|	11.152.1.100/31|	|	to_EXT_router_vrf_ADM|	Vrf_ADM|	PortChannel3|
|57|	1|	border-1-2|	Loopback0|	|	11.150.2.0/32|	|	router_id|	|	|
|58|	1|	border-1-2|	Loopback1|	|	11.150.1.100/32|	|	vtep|	|	|
|59|	1|	border-1-2|	Ethernet1|	25G|	11.2.1.11/31|	|	to_spine-1-1|	|	|
|60|	1|	border-1-2|	Ethernet2|	25G|	11.2.2.11/31|	|	to_spine-1-2|	|	|
|61|	1|	border-1-2|	Vlan120|	|	11.152.2.0/31|	|	to_INT_router_vrf_ADM|	Vrf_ADM|	PortChannel2|
|62|	1|	border-1-2|	Vlan220|	|	11.152.2.2/31|	|	to_INT_router_vrf_CAD|	Vrf_CAD|	PortChannel2|
|63|	1|	border-1-2|	Vlan320|	|	11.152.2.4/31|	|	to_INT_router_vrf_ASU|	Vrf_ASU|	PortChannel2|
|64|	1|	border-1-2|	Vlan920|	|	11.152.2.100/31|	|	to_EXT_router_vrf_ADM|	Vrf_ADM|	PortChannel3|
|65|	1|	int-router-1|	Loopback0|	|	11.200.1.0/32|	|	router_id|	|	|
|66|	1|	int-router-1|	Vlan110|	|	11.152.1.1/31|	|	to_border-1-1_vrf_ADM|	Vrf_ADM|	PortChannel1|
|67|	1|	int-router-1|	Vlan210|	|	11.152.1.3/31|	|	to_border-1-1_vrf_CAD|	Vrf_CAD|	PortChannel1|
|68|	1|	int-router-1|	Vlan210|	|	11.152.1.5/31|	|	to_border-1-1_vrf_ASU|	Vrf_ASU|	PortChannel1|
|69|	1|	int-router-1|	Vlan120|	|	11.152.2.1/31|	|	to_border-1-2_vrf_ADM|	Vrf_ADM|	PortChannel2|
|70|	1|	int-router-1|	Vlan220|	|	11.152.2.3/31|	|	to_border-1-2_vrf_CAD|	Vrf_CAD|	PortChannel2|
|71|	1|	int-router-1|	Vlan220|	|	11.152.2.5/31|	|	to_border-1-2_vrf_ASU|	Vrf_ASU|	PortChannel2|
|72|	1|	ext-router-1|	Loopback0|	|	11.250.1.0/32|	|	router_id|	|	|
|73|	1|	ext-router-1|	Loopback1|	|	100.100.100.1/32|	|	ext_router_id|	Vrf_EXT|	|
|74|	1|	ext-router-1|	Vlan910|	|	11.152.1.101/31|	|	to_border-1-1_vrf_ADM|	Vrf_ADM|	PortChannel1|
|75|	1|	ext-router-1|	Vlan920|	|	11.152.2.101/31|	|	to_border-1-2_vrf_ADM|	Vrf_ADM|	PortChannel2|
|76|	2|	spine-2-1|	Loopback0|	|	12.0.1.0/32|	|	router_id|	|	|
|77|	2|	spine-2-1|	Ethernet1|	25G|	12.2.1.0/31|	|	to_leaf-2-1|	|	|
|78|	2|	spine-2-1|	Ethernet2|	25G|	12.2.1.2/31|	|	to_leaf-2-2|	|	|
|79|	2|	spine-2-1|	Ethernet10|	25G|	11.102.1.1/31|	|	to_spine-1-1|	|	|
|80|	2|	spine-2-2|	Loopback0|	|	12.0.2.0/32|	|	router_id|	|	|
|81|	2|	spine-2-2|	Ethernet1|	25G|	12.2.2.0/31|	|	to_leaf-2-1|	|	|
|82|	2|	spine-2-2|	Ethernet2|	25G|	12.2.2.2/31|	|	to_leaf-2-2|	|	|
|83|	2|	spine-2-2|	Ethernet10|	25G|	11.102.2.1/31|	|	to_spine-1-2|	|	|
|84|	2|	leaf-2-1|	Loopback0|	|	12.1.1.0/32|	|	router_id|	|	|
|85|	2|	leaf-2-1|	Loopback1|	|	12.1.1.100/32|	|	vtep|	|	|
|86|	2|	leaf-2-1|	Ethernet1|	25G|	12.2.1.1/31|	|	to_spine-2-1|	|	|
|87|	2|	leaf-2-1|	Ethernet2|	25G|	12.2.2.1/31|	|	to_spine-2-2|	|	|
|88|	2|	leaf-2-1|	Vlan201|	|	10.4.27.254/22|	1|	cad_access_vlan|	Vrf_CAD|	PortChannel1, PortChannel2|
|89|	2|	leaf-2-1|	Vlan301|	|	10.8.255.254/16|	1|	asu_access_vlan|	Vrf_ASU|	PortChannel1, PortChannel3|
|90|	2|	leaf-2-2|	Loopback0|	|	12.1.2.0/32|	|	router_id|	|	|
|91|	2|	leaf-2-2|	Loopback1|	|	12.1.1.100/32|	|	vtep|	|	|
|92|	2|	leaf-2-2|	Ethernet1|	25G|	12.2.1.3/31|	|	to_spine-2-1|	|	|
|93|	2|	leaf-2-2|	Ethernet2|	25G|	12.2.2.3/31|	|	to_spine-2-2|	|	|
|94|	2|	leaf-2-2|	Vlan201|	|	10.4.27.254/22|	1|	cad_access_vlan|	Vrf_CAD|	PortChannel1, PortChannel2|
|95|	2|	leaf-2-2|	Vlan301|	|	10.8.255.254/16|	1|	asu_access_vlan|	Vrf_ASU|	PortChannel1, PortChannel3|

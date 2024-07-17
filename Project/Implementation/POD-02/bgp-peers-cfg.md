## Параметры BGP

### Параметры BGP-соседств

|POD|	hostname|	router ID|	VRF|	peer-group|	peer-group opts|	AF1|	AF1_opts|	AF2|	AF2_opts|	Neighbor|	Neighbor opts|
|--|--|--|--|--|--|--|--|--|--|--|--|
|2|	spine-2-1|	12.0.1.0|	|	LEAFS|	timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast| activate send-community both|	l2vpn evpn|	activate|	12.2.1.1|	remote-as 1220000001 description leaf-2-1_peer|
|2|	spine-2-1|	12.0.1.0|	|	LEAFS|	timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast| activate send-community both|	l2vpn evpn|	activate|	12.2.1.3|	remote-as 1220000001 description leaf-2-2_peer|
|2|	spine-2-1|	12.0.1.0|	|	POD_SPINES|	timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast| activate send-community both|	l2vpn evpn|	activate|	11.102.1.0|	remote-as 1110000000 description spine-1-1_peer|
|2|	spine-2-2|	12.0.20|	|	LEAFS|	timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast|	 activate send-community both| l2vpn evpn|	activate|	12.2.2.1|	remote-as 1220000001 description leaf-2-1_peer| 
|2|	spine-2-2|	12.0.20|	|	LEAFS|	timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast| activate send-community both|	l2vpn evpn|	activate|	11.2.2.3|	remote-as 1220000001 description leaf-2-2_peer|
|2|	spine-2-2|	12.0.20|	|	POD_SPINES|	timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast| activate send-community both|	l2vpn evpn|	activate|	11.102.2.0|	remote-as 1110000000 description spine-1-2_peer|
|2|	leaf-2-1|	12.1.1.0|	|	SPINES|	remote-as 1210000000 timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast|	activate allowas-in 2 send-community both|	l2vpn evpn|	activate|	12.2.1.0|	description spine-2-1_peer|
|2|	leaf-2-1|	12.1.1.0|	|	SPINES|	remote-as 1210000000 timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast|	activate allowas-in 2 send-community both|	l2vpn evpn|	activate|	12.2.2.0|	description spine-2-2_peer|
|2|	leaf-2-2|	12.1.2.0|	|	SPINES|	remote-as 1210000000 timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast|	activate allowas-in 2 send-community both|	l2vpn evpn|	activate|	12.2.1.2|	description spine-2-1_peer|
|2|	leaf-2-2|	12.1.2.0|	|	SPINES|	remote-as 1210000000 timers 3 9 timers connect 12 bfd advertisement-interval 0 capability extended-nexthop|	ipv4 unicast|	activate allowas-in 2 send-community both|	l2vpn evpn|	activate|	12.2.2.2|	description spine-2-2_peer|

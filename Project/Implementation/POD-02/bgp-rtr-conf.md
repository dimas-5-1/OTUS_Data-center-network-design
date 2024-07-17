## Параметры BGP

### Параметры маршрутизаторов

|POD|	hostname|	router ID|	ASN|	VRF|	Router opts|	AF1|	AF1_opts|	AF2|	AF2_opts|
|--|--|--|--|--|--|--|--|--|--|
|1|	ext-router-1|	11.250.1.0|	64555|	Vrf_ADM|log-neighbor-changes  timers 3 9|	ipv4 unicast|	redistribute connected maximum-paths 2 maximum-paths ibgp 1 import vrf Vrf_EXT|	|	|
|2|	spine-2-1|	12.0.1.0|	1210000000|	|log-neighbor-changes  bestpath as-path multipath-relax timers 3 9|	ipv4 unicast|	  redistribute connected   maximum-paths 2  maximum-paths ibgp 1|	|	|
|2|	spine-2-2|	12.0.2.0|	1210000000|	|log-neighbor-changes bestpath as-path multipath-relax timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	|	|
|2|	leaf-2-1|	12.1.1.0|	1220000001|	|log-neighbor-changes bestpath as-path multipath-relax timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	l2vpn evpn|	advertise-all-vni vni 20101 route-target both 1020000000:201 vni 30101 route-target both 1020000000:301||2|	leaf-2-1|	12.1.1.0|	1220000001|	Vrf_CAD|log-neighbor-changes timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	l2vpn evpn|	advertise ipv4 unicast RD: 12.1.1.0:2000 RT both: 1020000000:2000 RT import: 1030000000:2000|
|2|	leaf-2-1|	12.1.1.0|	1220000001|	Vrf_ASU|log-neighbor-changes timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	l2vpn evpn|	advertise ipv4 unicast  RD: 12.1.1.0:3000 RT both: 1020000000:3000 RT import: 1030000000:3000|
|2|	leaf-2-2|	12.1.2.0|	1220000001|	|log-neighbor-changes bestpath as-path multipath-relax timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	l2vpn evpn|	advertise-all-vni vni 20101 route-target both 1020000000:201 vni 30101 route-target both 1020000000:301|
|2|	leaf-2-2|	12.1.2.0|	1220000001|	Vrf_CAD|log-neighbor-changes timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	l2vpn evpn|	advertise ipv4 unicast  RD: 12.1.2.0:2000 RT both: 1020000000:2000 RT import: 1030000000:2000|
|2|	leaf-2-2|	12.1.2.0|	1220000001|	Vrf_ASU|log-neighbor-changes timers 3 9|	ipv4 unicast|	  redistribute connected  maximum-paths 2  maximum-paths ibgp 1|	l2vpn evpn|	advertise ipv4 unicast  RD: 12.1.2.0:3000 RT both: 1020000000:3000 RT import: 1030000000:3000|

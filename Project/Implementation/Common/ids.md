## Идентификаторы маршрутизаторов
---

|  DC  |	POD  |	Router  |	RID  |	Interface  |	BGP ASN  |	VRF1  |	VRF2  |	VRF3  |	VRF4  |
|--|--|--|--|--|--|--|--|--|--|
|  1  |	1  |	spine-1-1  |	11.0.1.0  |	Loopback 0  |	1110000000  |	default  |	  |	  |	  |
|  1  |	1  |	spine-1-2  |	11.0.2.0  |	Loopback 0  |	1110000000  |	default  |	  |	  |	  |
|  1  |	1  |	leaf-1-1  |	11.1.1.0  |	Loopback 0  |	1120000001  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	leaf-1-2  |	11.1.2.0  |	Loopback 0  |	1120000001  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	leaf-1-3  |	11.1.3.0  |	Loopback 0  |	1120000002  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	leaf-1-4  |	11.1.4.0  |	Loopback 0  |	1120000002  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	border-1-1  |	11.150.1.0  |	Loopback 0  |	1130000001  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	border-1-2  |	11.150.2.0  |	Loopback 0  |	1130000002  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	Int-router-1  |	11.200.1.0  |	Loopback 0  |	65000  |	default  |	Vrf_ADM  |	Vrf_CAD  |	Vrf_ASU  |
|  1  |	1  |	Ext-router-1  |	11.250.1.0  |	Loopback 0  |	64555  |	default  |	Vrf_ADM  |	  |	  |
|  1  |	2  |	spine-2-1  |	12.0.1.0  |	Loopback 0  |	1210000000  |	default  |	  |	  |	  |
|  1  |	2  |	spine-2-2  |	12.0.2.0  |	Loopback 0  |	1210000000  |	default  |	  |	  |	  |
|  1  |	2  |	leaf-2-1  |	12.1.1.0  |	Loopback 0  |	1220000001  |	default  |	Vrf_CAD  |	Vrf_ASU  |	  |
|  1  |	2  |	leaf-2-2  |	12.1.2.0  |	Loopback 0  |	1220000001  |	default  |	Vrf_CAD  |	Vrf_ASU  |	  |


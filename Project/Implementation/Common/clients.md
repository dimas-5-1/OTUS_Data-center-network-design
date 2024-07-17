# Идентификаторы клиентских сервисов
## VXLAN
|Сегмент|	Network address|	Anycast GW|	Access Vlan |	L3VNI Vlan |	L2VNI |	L3VNI |	Vrf |
|--|--|--|--|--|--|--|--|
|CRM|	10.4.8.0/22|	10.4.11.254/22|	101|	1000|	10101|	10000|	Vrf_ADM|
|1C|	10.4.12.0/22|	10.4.15.254/22|	102|	1000|	10201|	10000|	Vrf_ADM|
|CAD|	10.4.24.0/22|	10.4.27.254/22|	201|	2000|	20101|	20000|	Vrf_CAD|

## IP адресация
|Host|	L3 addr|	static route|
|--|--|--|
|CRM_Master|	10.4.8.1/22|	0.0.0.0/0 next-hop 10.4.11.254/22|
|CRM_Slave|	10.4.8.2/22|	0.0.0.0/0 next-hop 10.4.11.254/22|
|1C_Master|	10.4.12.1/22|	0.0.0.0/0 next-hop 10.4.15.254/22|
|1C_Slave|	10.4.12.2/22|	0.0.0.0/0 next-hop 10.4.15.254/22|
|CAD_Master|	10.4.24.1/22|	0.0.0.0/0 next-hop 10.4.27.254/22|
|CAD_Slave|	10.4.24.2/22|	0.0.0.0/0 next-hop 10.4.27.254/22|
|ASU_Master|	10.8.0.1/16|	0.0.0.0/0 next-hop 10.8.255.254/16|
|ASU_Slave|	10.8.0.2/16|	0.0.0.0/0 next-hop 10.8.255.254/16|
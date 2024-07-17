# Линки ЦОД

|N|	POD|	Node_A|	Node_Z|	Layer|	Type|	Note|	Allowed VLANS|	interface_A|	interface_Z|	BW|	is_LAG|	parent_port_A|	parent_port_Z|	L3_addr_A|	L3_addr_Z|
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
|1|	1|	spine-1-1|	leaf-1-1|	3|	|	|	|	Ethernet1|	Ethernet1|	25G|	|	|	|	11.2.1.0/31|	11.2.1.1/31|
|2|	1|	spine-1-1|	leaf-1-2|	3|	|	|	|	Ethernet2|	Ethernet1|	25G|	|	|	|	11.2.1.2/31|	11.2.1.3/31|
|3|	1|	spine-1-1|	leaf-1-3|	3|	|	|	|	Ethernet3|	Ethernet1|	25G|	|	|	|	11.2.1.4/31|	11.2.1.5/31|
|4|	1|	spine-1-1|	leaf-1-4|	3|	|	|	|	Ethernet4|	Ethernet1|	25G|	|	|	|	11.2.1.6/31|	11.2.1.7/31|
|5|	1|	spine-1-1|	border-1-1|	3|	|	|	|	Ethernet5|	Ethernet1|	25G|	|	|	|	11.2.1.8/31|	11.2.1.9/31|
|6|	1|	spine-1-1|	border-1-2|	3|	|	|	|	Ethernet6|	Ethernet1|	25G|	|	|	|	11.2.1.10/31|	11.2.1.11/31|
|7|	1-2|	spine-1-1|	spine-2-1|	3|	|	|	|	Ethernet10|	Ethernet10|	25G|	|	|	|	11.102.1.0/31|	11.102.1.1/31|
|8|	1|	spine-1-2|	leaf-1-1|	3|	|	|	|	Ethernet1|	Ethernet2|	25G|	|	|	|	11.2.2.0/31|	11.2.2.1/31|
|9|	1|	spine-1-2|	leaf-1-2|	3|	|	|	|	Ethernet2|	Ethernet2|	25G|	|	|	|	11.2.2.2/31|	11.2.2.3/31|
|10|	1|	spine-1-2|	leaf-1-3|	3|	|	|	|	Ethernet3|	Ethernet2|	25G|	|	|	|	11.2.2.4/31|	11.2.2.5/31|
|11|	1|	spine-1-2|	leaf-1-4|	3|	|	|	|	Ethernet4|	Ethernet2|	25G|	|	|	|	11.2.2.6/31|	11.2.2.7/31|
|12|	1|	spine-1-2|	border-1-1|	3|	|	|	|	Ethernet5|	Ethernet2|	25G|	|	|	|	11.2.2.8/31|	11.2.2.9/31|
|13|	1|	spine-1-2|	border-1-2|	3|	|	|	|	Ethernet6|	Ethernet2|	25G|	|	|	|	11.2.2.10/31|	11.2.2.11/31|
|14|	1-2|	spine-1-2|	spine-2-2|	3|	|	|	|	Ethernet10|	Ethernet10|	25G|	|	|	|	11.102.2.0/31|	11.102.2.1/31|
|15|	1|	leaf-1-1|	leaf-1-2|	2|	trunk|	mclag peer-link|	101, 102, 201, 301, 1000,2000, 3000|	PortChannel1|	PortChannel1|	20G|	1|	|	|	|	|
|16|	1|	leaf-1-1|	leaf-1-2|	2|	lag member|	|	|	Ethernet4|	Ethernet4|	10G|	|	PortChannel1|	PortChannel1|	|	|
|17|	1|	leaf-1-1|	leaf-1-2|	2|	lag member|	|	|	Ethernet5|	Ethernet5|	10G|	|	PortChannel1|	PortChannel1|	|	|
|18|	1|	leaf-1-1|	CRM_Master|	2|	access|	mclag portchannel|	101|	PortChannel2|	|	1G|	1|	|	|	|	|
|19|	1|	leaf-1-1|	CRM_Master|	2|	lag member|	|	|	Ethernet8|	Ethernet1|	1G|	|	PortChannel2|	PortChannel1|	|	|
|20|	1|	leaf-1-1|	1C_Master|	2|	access|	mclag portchannel|	102|	PortChannel3|	|	1G|	1|	|	|	|	|
|21|	1|	leaf-1-1|	1C_Master|	2|	lag member|	|	|	Ethernet9|	Ethernet1|	1G|	|	PortChannel3|	PortChannel1|	|	|
|22|	1|	leaf-1-1|	CAD_Master|	2|	access|	mclag portchannel|	201|	PortChannel4|	|	1G|	1|	|	|	|	|
|23|	1|	leaf-1-1|	CAD_Master|	2|	lag member|	|	|	Ethernet10|	Ethernet1|	1G|	|	PortChannel4|	PortChannel1|	|	|
|24|	1|	leaf-1-2|	CRM_Master|	2|	access|	mclag portchannel|	101|	PortChannel2|	|	1G|	1|	|	|	|	|
|25|	1|	leaf-1-2|	CRM_Master|	2|	lag member|	|	|	Ethernet8|	Ethernet2|	1G|	|	PortChannel2|	PortChannel1|	|	|
|26|	1|	leaf-1-2|	1C_Master|	2|	access|	mclag portchannel|	102|	PortChannel3|	|	1G|	1|	|	|	|	|
|27|	1|	leaf-1-2|	1C_Master|	2|	lag member|	|	|	Ethernet9|	Ethernet2|	1G|	|	PortChannel3|	PortChannel1|	|	|
|28|	1|	leaf-1-2|	CAD_Master|	2|	access|	mclag portchannel|	201|	PortChannel4|	|	1G|	1|	|	|	|	|
|29|	1|	leaf-1-2|	CAD_Master|	2|	lag member|	|	|	Ethernet10|	Ethernet2|	1G|	|	PortChannel4|	PortChannel1|	|	|
|30|	1|	leaf-1-3|	leaf-1-4|	2|	trunk|	mclag peer-link|	101, 102, 201, 301, 1000,2000, 3000|	PortChannel1|	PortChannel1|	20G|	1|	|	|	|	|
|31|	1|	leaf-1-3|	leaf-1-4|	2|	lag member|	|	|	Ethernet4|	Ethernet4|	10G|	|	PortChannel1|	PortChannel1|	|	|
|32|	1|	leaf-1-3|	leaf-1-4|	2|	lag member|	|	|	Ethernet5|	Ethernet5|	10G|	|	PortChannel1|	PortChannel1|	|	|
|33|	1|	leaf-1-3|	CRM_Slave|	2|	access|	mclag portchannel|	101|	PortChannel2|	|	1G|	1|	|	|	|	|
|34|	1|	leaf-1-3|	CRM_Slave|	2|	lag member|	|	|	Ethernet8|	Ethernet1|	1G|	|	PortChannel2|	PortChannel1|	|	|
|35|	1|	leaf-1-3|	1C_Slave|	2|	access|	mclag portchannel|	102|	PortChannel3|	|	1G|	1|	|	|	|	|
|36|	1|	leaf-1-3|	1C_Slave|	2|	lag member|	|	|	Ethernet9|	Ethernet1|	1G|	|	PortChannel3|	PortChannel1|	|	|
|37|	1|	leaf-1-3|	ASU_Slave|	2|	access|	mclag portchannel|	301|	PortChannel4|	|	1G|	1|	|	|	|	|
|38|	1|	leaf-1-3|	ASU_Slave|	2|	lag member|	|	|	Ethernet10|	Ethernet1|	1G|	|	PortChannel4|	PortChannel1|	|	|
|39|	1|	leaf-1-4|	CRM_Slave|	2|	access|	mclag portchannel|	101|	PortChannel2|	|	1G|	1|	|	|	|	|
|40|	1|	leaf-1-4|	CRM_Slave|	2|	lag member|	|	|	Ethernet8|	Ethernet2|	1G|	|	PortChannel2|	PortChannel1|	|	|
|41|	1|	leaf-1-4|	1C_Slave|	2|	access|	mclag portchannel|	102|	PortChannel3|	|	1G|	1|	|	|	|	|
|42|	1|	leaf-1-4|	1C_Slave|	2|	lag member|	|	|	Ethernet9|	Ethernet2|	1G|	|	PortChannel3|	PortChannel1|	|	|
|43|	1|	leaf-1-4|	ASU_Slave|	2|	access|	mclag portchannel|	301|	PortChannel4|	|	1G|	1|	|	|	|	|
|44|	1|	leaf-1-4|	ASU_Slave|	2|	lag member|	|	|	Ethernet10|	Ethernet2|	1G|	|	PortChannel4|	PortChannel1|	|	|
|48|	1|	border-1-1|	Int-router-1|	2|	trunk|	|	110, 210, 310|	PortChannel2|	PortChannel1|	10G|	1|	|	|	|	|
|49|	1|	border-1-1|	Int-router-1|	2|	lag member|	|	|	Ethernet8|	Ethernet1|	10G|	|	PortChannel2|	PortChannel1|	|	|
|50|	1|	border-1-1|	Ext-router-1|	2|	trunk|	|	910|	PortChannel3|	PortChannel1|	10G|	1|	|	|	|	|
|51|	1|	border-1-1|	Ext-router-1|	2|	lag member|	|	|	Ethernet9|	Ethernet1|	10G|	|	PortChannel3|	PortChannel1|	|	|
|52|	1|	border-1-2|	Int-router-1|	2|	trunk|	|	120, 220, 320|	PortChannel2|	PortChannel2|	10G|	1|	|	|	|	|
|53|	1|	border-1-2|	Int-router-1|	2|	lag member|	|	|	Ethernet8|	Ethernet2|	10G|	|	PortChannel2|	PortChannel2|	|	|
|54|	1|	border-1-2|	Ext-router-1|	2|	trunk|	|	910|	PortChannel3|	PortChannel2|	10G|	1|	|	|	|	|
|55|	1|	border-1-2|	Ext-router-1|	2|	lag member|	|	|	Ethernet9|	Ethernet2|	10G|	|	PortChannel3|	PortChannel2|	|	|
|56|	2|	spine-2-1|	leaf-2-1|	3|	|	|	|	Ethernet1|	Ethernet1|	25G|	|	|	|	12.2.1.0/31|	12.2.1.1/31|
|57|	2|	spine-2-1|	leaf-2-2|	3|	|	|	|	Ethernet2|	Ethernet1|	25G|	|	|	|	12.2.1.2/31|	12.2.1.3/31|
|58|	2|	spine-2-2|	leaf-2-1|	3|	|	|	|	Ethernet1|	Ethernet2|	25G|	|	|	|	12.2.2.0/31|	12.2.2.1/31|
|59|	2|	spine-2-2|	leaf-2-2|	3|	|	|	|	Ethernet2|	Ethernet2|	25G|	|	|	|	12.2.2.2/31|	12.2.2.3/31|
|60|	2|	leaf-2-1|	leaf-2-2|	2|	trunk|	mclag peer-link|	201, 301, 2000, 3000|	PortChannel1|	PortChannel1|	20G|	1|	|	|	|	|
|61|	2|	leaf-2-1|	leaf-2-2|	2|	lag member|	|	|	Ethernet4|	Ethernet4|	10G|	|	PortChannel1|	PortChannel1|	|	|
|62|	2|	leaf-2-1|	leaf-2-2|	2|	lag member|	|	|	Ethernet5|	Ethernet5|	10G|	|	PortChannel1|	PortChannel1|	|	|
|63|	2|	leaf-2-1|	CAD_Slave|	2|	access|	mclag portchannel|	201|	PortChannel2|	|	1G|	1|	|	|	|	|
|64|	2|	leaf-2-1|	CAD_Slave|	2|	lag member|	|	|	Ethernet5|	Ethernet1|	1G|	|	PortChannel2|	PortChannel1|	|	|
|65|	2|	leaf-2-1|	ASU_Master|	2|	access|	mclag portchannel|	301|	PortChannel3|	|	1G|	1|	|	|	|	|
|66|	2|	leaf-2-1|	ASU_Master|	2|	lag member|	|	|	Ethernet6|	Ethernet1|	1G|	|	PortChannel3|	PortChannel1|	|	|
|67|	2|	leaf-2-2|	CAD_Slave|	2|	access|	mclag portchannel|	201|	PortChannel2|	|	1G|	1|	|	|	|	|
|68|	2|	leaf-2-2|	CAD_Slave|	2|	lag member|	|	|	Ethernet5|	Ethernet1|	1G|	|	PortChannel2|	PortChannel1|	|	|
|69|	2|	leaf-2-2|	ASU_Master|	2|	access|	mclag portchannel|	301|	PortChannel3|	|	1G|	1|	|	|	|	|
|70|	2|	leaf-2-2|	ASU_Master|	2|	lag member|	|	|	Ethernet6|	Ethernet1|	1G|	|	PortChannel3|	PortChannel1|	|	|

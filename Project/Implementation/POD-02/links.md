# Линки. POD-02

|	Node_A|	Node_Z|	Layer|	Type|	Note|	Allowed VLANS|	interface_A|	interface_Z|	BW|	is_LAG|	parent_port_A|	parent_port_Z|	L3_addr_A|	L3_addr_Z|
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
|spine-1-1|	spine-2-1|	3|	|	|	|	Ethernet10|	Ethernet10|	25G|	|	|	|	11.102.1.0/31|	11.102.1.1/31|
|spine-1-2|	spine-2-2|	3|	|	|	|	Ethernet10|	Ethernet10|	25G|	|	|	|	11.102.2.0/31|	11.102.2.1/31|
|	spine-2-1|	leaf-2-1|	3|	|	|	|	Ethernet1|	Ethernet1|	25G|	|	|	|	12.2.1.0/31|	12.2.1.1/31|
|	spine-2-1|	leaf-2-2|	3|	|	|	|	Ethernet2|	Ethernet1|	25G|	|	|	|	12.2.1.2/31|	12.2.1.3/31|
|	spine-2-2|	leaf-2-1|	3|	|	|	|	Ethernet1|	Ethernet2|	25G|	|	|	|	12.2.2.0/31|	12.2.2.1/31|
|	spine-2-2|	leaf-2-2|	3|	|	|	|	Ethernet2|	Ethernet2|	25G|	|	|	|	12.2.2.2/31|	12.2.2.3/31|
|	leaf-2-1|	leaf-2-2|	2|	trunk|	mclag peer-link|	201, 301, 2000, 3000|	PortChannel1|	PortChannel1|	20G|	1|	|	|	|	|
|	leaf-2-1|	leaf-2-2|	2|	lag member|	|	|	Ethernet4|	Ethernet4|	10G|	|	PortChannel1|	PortChannel1|	|	|
|	leaf-2-1|	leaf-2-2|	2|	lag member|	|	|	Ethernet5|	Ethernet5|	10G|	|	PortChannel1|	PortChannel1|	|	|
|	leaf-2-1|	CAD_Slave|	2|	access|	mclag portchannel|	201|	PortChannel2|	|	1G|	1|	|	|	|	|
|	leaf-2-1|	CAD_Slave|	2|	lag member|	|	|	Ethernet5|	Ethernet1|	1G|	|	PortChannel2|	PortChannel1|	|	|
|	leaf-2-1|	ASU_Master|	2|	access|	mclag portchannel|	301|	PortChannel3|	|	1G|	1|	|	|	|	|
|	leaf-2-1|	ASU_Master|	2|	lag member|	|	|	Ethernet6|	Ethernet1|	1G|	|	PortChannel3|	PortChannel1|	|	|
|	leaf-2-2|	CAD_Slave|	2|	access|	mclag portchannel|	201|	PortChannel2|	|	1G|	1|	|	|	|	|
|	leaf-2-2|	CAD_Slave|	2|	lag member|	|	|	Ethernet5|	Ethernet1|	1G|	|	PortChannel2|	PortChannel1|	|	|
|	leaf-2-2|	ASU_Master|	2|	access|	mclag portchannel|	301|	PortChannel3|	|	1G|	1|	|	|	|	|
|	leaf-2-2|	ASU_Master|	2|	lag member|	|	|	Ethernet6|	Ethernet1|	1G|	|	PortChannel3|	PortChannel1|	|	|

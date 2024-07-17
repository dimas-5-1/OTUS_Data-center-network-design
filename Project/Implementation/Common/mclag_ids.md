## Идентификаторы MCLAG

|hostname|	gateway-mac|	mclag domain|	source-ip|	peer-ip |	peer-link|	mclag-system-mac|	keepalive-interval|	session-timeout|	delay-restore|	MCLAG PortChannels|
|--|--|--|--|--|--|--|--|--|--|--|
|leaf-1-1|	00:11:00:11:00:11|	1|	11.1.1.0|	11.1.2.0|	PortChannel 1 |	00:00:a1:a1:a1:a1|	1|	30|	90|	2,3,4|
|leaf-1-2|	00:11:00:11:00:11|	1|	11.1.2.0|	11.1.1.0|	PortChannel 1 |	00:00:a1:a1:a1:a1|	1|	30|	90|	2,3,4|
|leaf-1-3|	00:12:00:12:00:12|	1|	11.1.3.0|	11.1.4.0|	PortChannel 1 |	00:00:a2:a2:a2:a2|	1|	30|	90|	2,3,4|
|leaf-1-4|	00:12:00:12:00:12|	1|	11.1.4.0|	11.1.3.0|	PortChannel 1 |	00:00:a2:a2:a2:a2|	1|	30|	90|	2,3,4|
|leaf-2-1|	00:21:00:21:00:21|	1|	12.1.1.0|	12.1.2.0|	PortChannel 1 |	00:00:b1:b1:b1:b1|	1|	30|	90|	2, 3|
|leaf-2-2|	00:21:00:21:00:21|	1|	12.1.2.0|	12.1.1.0|	PortChannel 1 |	00:00:b1:b1:b1:b1|	1|	30|	90|	2, 3|

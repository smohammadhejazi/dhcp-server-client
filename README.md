# DHCP server and client
This project contains a DHCP server which can dynamically set IP address for clients.
Each client continuously send DHCP discover message when its IP address expires or doesn't have any; after receiving DHCP offer from server,  then sends DHCP request and waits for DHCP ack from server.

## Server features
When server starts off, it reads all the configs from configs.json which includes lease_time of the IP addresses, reservation list for IPs, black list of MAC addresses and also two modes for IP pool specification.
- Range:
IP pool = [from, to]
- Subnet:
IP pool = [ip_block, all the IPs in the subnet

## Client features
If client doesn't receive response from server, the time that it waits after the next DHCP discover message increases by wait_time \*= random(0.5, 1) \* 2

## How it works
In order to run the server, simply do:
```sh
python server.py
```
then we can run the client:
```sh
python client.py <host name> <MAC address>
```


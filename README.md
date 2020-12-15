# aws-educate-test-2

## Simple Routing in AWS

- 3 Subnets - 172.31.101.0/24, 172.31.102.0/24, 172.31.103.0/24
- 3 EC2 Instances - 2 Clients in the 101 and 102 subnets, and a Router in the 103 Subnet
- Security Groups such that the 101 and 102 client can only talk to the router

## Setup Scripts [user_data]

- Turn on IP Forwarding on the router
```
echo 'net.ipv4.ip_forward=1' | sudo tee -a /etc/sysctl.conf
sysctl -p /etc/sysctl.conf
```

- Add routes to the route tables in the clients
```
sudo route add -net 172.31.10x.0 netmask 255.255.255.0 gw 172.31.y.z
```
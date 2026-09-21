## Jeremy's IT Lab - Day 11 Part 2: Configuring Static Rou[day 11 part(0)]tes

[day 11 part 2 topology](<./day-11-part(2)-topologie.png>)

## Objective

Configure default static routes and floating static routes to establish backup paths and handle link failures.

Device Interfaces & Subnets
Segment Subnet
PC1 LAN 192.168.1.0/24
R1-R2 Primary 192.168.12.0/24
R1-R3 Backup 192.168.13.0/24
R2-R3 192.168.23.0/24
PC2 LAN 192.168.3.0/24
Static Route Configurations
R1
ip route 0.0.0.0 0.0.0.0 192.168.12.2
ip route 0.0.0.0 0.0.0.0 192.168.13.3 10
R2
ip route 192.168.3.0 255.255.255.0 192.168.23.3

ip route 192.168.1.0 255.255.255.0 192.168.23.2
ip route 192.168.1.0 255.255.255.0 192.168.13.1 10
Verification Commands
show ip route
show ip route static
Normal state on R1: S\* 0.0.0.0/0 [1/0] via 192.168.12.2

Failover Test
Shut down R1's interface connected to 192.168.12.0/24.

Check show ip route on R1. The floating route should now appear:
S\* 0.0.0.0/0 [10/0] via 192.168.13.3

Ping from PC1 to PC2 to confirm traffic uses the backup path.

Re-enable the interface. The primary route returns.

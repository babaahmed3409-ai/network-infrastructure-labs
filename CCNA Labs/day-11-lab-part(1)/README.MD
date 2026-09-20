## Jeremy's IT Lab CCNA — Day 11 Lab: Configuring Static Routes (Part 1)

This folder contains the network topology file, configuration commands, and verification steps for Day 11 Lab.

![Day 9 Topology](<day-11-lab-part(1)-topology.png>)

## Objective

- Configure static routes between R1, R2, and R3 to establish full connectivity.

## Device Interfaces & Subnets

- PC1 Network: 192.168.1.0/24
- R1-R2 Link Network: 192.168.12.0/24
- R2-R3 Link Network: 192.168.13.0/24
- PC2 Network: 192.168.3.0/24

---

## Static Route Configurations## Router 2 (R2)

R2# configure terminal
R2(config)# ip route 192.168.1.0 255.255.255.0 192.168.12.1
R2(config)# ip route 192.168.3.0 255.255.255.0 192.168.13.3

## Router 3 (R3)

R3# configure terminal
R3(config)# ip route 192.168.1.0 255.255.255.0 192.168.13.2

---

## Verification Commands

- show ip route
- show ip interface brief

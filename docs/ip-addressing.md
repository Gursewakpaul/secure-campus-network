# IP Addressing

## Infrastructure
| Device   | Interface | IP Address      | Mask / Prefix   | Notes                    |
|----------|-----------|-----------------|-----------------|--------------------------|
| CORE-SW1 | Gi0/1 (routed) | 10.0.0.1   | 255.255.255.252 | Link to R1               |
| R1       | Gi0/0     | 10.0.0.2        | 255.255.255.252 | Inside, default route in |
| R1       | Gi0/1     | 203.0.113.1     | 255.255.255.252 | Outside (NAT)            |
| ISP      | Gi0/0     | 203.0.113.2     | 255.255.255.252 | Simulated ISP            |
| ACC-SW1  | VLAN 99   | 192.168.99.11   | 255.255.255.0   | GW 192.168.99.1          |
| ACC-SW2  | VLAN 99   | 192.168.99.12   | 255.255.255.0   | GW 192.168.99.1          |

## Hosts
| Device       | VLAN | Switch  | Addressing                 |
|--------------|------|---------|----------------------------|
| STAFF-PC1    | 10   | ACC-SW1 | DHCP                       |
| STAFF-PC2    | 10   | ACC-SW2 | DHCP                       |
| GUEST-PC1    | 20   | ACC-SW1 | DHCP                       |
| GUEST-PC2    | 20   | ACC-SW2 | DHCP                       |
| ATTACKER-PC  | 20   | ACC-SW2 | DHCP (used for attack tests)|
| ADMIN-PC     | 99   | ACC-SW1 | Static 192.168.99.50       |
| WEB-SRV1     | 30   | ACC-SW1 | Static 192.168.30.10       |

## DHCP Pools (on CORE-SW1)
| VLAN | Pool              | Excluded       |
|------|-------------------|----------------|
| 10   | 192.168.10.0/24   | .1 - .10       |
| 20   | 192.168.20.0/24   | .1 - .10       |
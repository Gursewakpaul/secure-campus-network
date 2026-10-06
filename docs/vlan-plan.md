# VLAN Plan

| VLAN | Name       | Subnet            | Gateway (SVI on CORE-SW1) | Purpose                     |
|------|------------|-------------------|---------------------------|-----------------------------|
| 10   | Staff      | 192.168.10.0/24   | 192.168.10.1              | Employee workstations       |
| 20   | Guest      | 192.168.20.0/24   | 192.168.20.1              | Untrusted guest devices     |
| 30   | Servers    | 192.168.30.0/24   | 192.168.30.1              | Internal web server         |
| 99   | Management | 192.168.99.0/24   | 192.168.99.1              | Switch/router management    |
| 999  | Native     | none              | none                      | Unused native VLAN on trunks|

## Access Policy (ACLs)
- Staff -> Servers: permitted
- Staff -> Internet: permitted (via NAT on R1)
- Guest -> Internet: permitted
- Guest -> Staff, Servers, Management: denied
- Management VLAN: reachable only from the Admin PC

## Layer 2 Security
- Trunks: native VLAN 999, DTP disabled, only required VLANs allowed
- Access ports: PortFast + BPDU Guard, port security (max 2 MACs, shutdown on violation)
- DHCP snooping on VLANs 10, 20; trusted ports = uplinks to CORE-SW1
- Dynamic ARP Inspection on VLANs 10, 20
- Unused ports: shut down, placed in VLAN 999
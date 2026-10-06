# Secure Campus Network

Segmented enterprise network built in Cisco Packet Tracer with Layer 2 and Layer 3 security controls.

## Topology

![Topology](topology/topology.png)

## Features

- VLAN segmentation with inter-VLAN routing
- DHCP, NAT, and redundant uplinks (Rapid PVST+, EtherChannel)
- Port security, DHCP snooping, and Dynamic ARP Inspection
- ACL-based access control between VLANs
- SSH-only device management with local AAA

## Design

- [VLAN plan](docs/vlan-plan.md)
- [IP addressing table](docs/ip-addressing.md)

## Security Testing

Attack simulations and results are documented in [test results](docs/test-results.md).

## How to Open

Open `topology/campus-network.pkt` in Cisco Packet Tracer 8.x.

## Lessons Learned / Future Improvements

- TBD
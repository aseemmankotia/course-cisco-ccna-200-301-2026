## Chapter 1 Cheat Sheet: Network Components, Topologies, Cabling

### Device Roles
| Device | Function |
|---|---|
| Router | Inter-network L3 routing, WAN connectivity, NAT |
| L2 Switch | Intra-VLAN switching, MAC address table |
| L3 Switch | Inter-VLAN routing (SVIs), fast ASIC-based, no native WAN |
| Firewall | Stateful inspection, zone-based policy |
| AP (lightweight) | Wireless bridge, managed by WLC via CAPWAP |
| WLC | Centralized AP management, RF, roaming |
| PoE device | Powered over Ethernet (camera, phone, AP) |

### Topologies
| Topology | Use Case | Key Trait |
|---|---|---|
| 3-tier | Large campus | Core / Distribution / Access layers |
| 2-tier (collapsed core) | Small/medium campus | Core+Distribution merged / Access |
| Spine-leaf | Data center | Every leaf ↔ every spine, no leaf-leaf/spine-spine links, predictable latency |
| Hub-and-spoke | WAN | Central hub, remote spokes, simple but hub is SPOF |
| Full mesh | WAN/DC | Every node connects to every other, high redundancy, costly |

### Cabling Comparison
| Type | Distance | Speed | Notes |
|---|---|---|---|
| UTP Cat5e | 100m | 1Gbps | Legacy, no shielding |
| UTP Cat6 | 100m (1G) / 55m (10G) | Up to 10Gbps | Distance drops sharply at 10G |
| UTP Cat6a | 100m | 10Gbps | Minimum standard for reliable 10GBASE-T |
| Multimode Fiber (MMF) | ~300-550m | 10G+ | LED/laser, orange/aqua, cheaper optics |
| Single-mode Fiber (SMF) | 10s of km | 10G-100G+ | Laser only, yellow jacket, long-haul |

### PoE Standards
| Standard | Name | Power at Source | Power at Device |
|---|---|---|---|
| 802.3af | PoE | 15.4W | 12.95W |
| 802.3at | PoE+ | 30W | 25.5W |
| 802.3bt Type 3 | UPOE | 60W | 51W |
| 802.3bt Type 4 | UPOE+ | 100W | 71.3W |

**PoE Budget Formula:** Total Switch Budget ÷ Per-Device Draw = Max Devices (round DOWN)

### On-Prem vs Cloud
| Aspect | On-Prem | Cloud |
|---|---|---|
| Ownership | Organization | Third-party provider |
| Cost Model | CapEx | OpEx |
| Scalability | Manual, hardware-bound | Elastic, on-demand |

### Key Troubleshooting Commands
- `show interfaces` — check CRC errors, collisions, duplex mismatches
- `show power inline` — verify PoE allocation per port
- `show cdp neighbors` — verify physical topology/connections

### Common Exam Traps
1. Router vs L3 switch — L3 switch usually lacks WAN interfaces/NAT capability.
2. Multimode vs single-mode confused by color coding alone — always verify by distance/laser requirement.
3. PoE budget miscalculated using per-port max instead of total switch power budget.

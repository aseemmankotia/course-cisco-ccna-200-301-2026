# Chapter 2 Cheat Sheet: Subnetting, VLSM, IPv6, TCP/UDP

## VLSM Quick Reference
| CIDR | Mask | Usable Hosts | Block Size |
|---|---|---|---|
| /24 | 255.255.255.0 | 254 | 256 |
| /25 | 255.255.255.128 | 126 | 128 |
| /26 | 255.255.255.192 | 62 | 64 |
| /27 | 255.255.255.224 | 30 | 32 |
| /28 | 255.255.255.240 | 14 | 16 |
| /29 | 255.255.255.248 | 6 | 8 |
| /30 | 255.255.255.252 | 2 | 4 |

**VLSM rule:** subnet largest host requirement first, align each new subnet to its own block boundary, never overlap ranges.

## IPv6 Address Types
| Type | Prefix | Purpose |
|---|---|---|
| Global unicast | 2000::/3 | Internet-routable |
| Link-local | FE80::/10 | On-link only, auto-assigned |
| Unique local | FC00::/7 (FD00::/8) | Private, RFC1918 equivalent |
| Multicast | FF00::/8 | One-to-many; replaces broadcast (FF02::1 = all nodes, FF02::2 = all routers) |
| Anycast | (from unicast space) | One-to-nearest |

**Shortening rules:** drop leading zeros per hextet; replace ONE longest run of all-zero hextets with `::`.

## TCP vs UDP
| Feature | TCP | UDP |
|---|---|---|
| Connection | Handshake (SYN/SYN-ACK/ACK) | Connectionless |
| Reliability | Guaranteed, ordered | Best-effort |
| Overhead | Higher | Lower |
| Use cases | HTTP, FTP, SSH | DNS queries, DHCP, VoIP, video |

## Wireless Basics
| Item | Detail |
|---|---|
| 2.4 GHz non-overlap channels (US) | 1, 6, 11 |
| 5 GHz | More channels, less interference, shorter range |
| SSID | Broadcast network name; must match on client/AP |
| Encryption | WPA2 (AES-CCMP), WPA3 (SAE) — avoid WEP/WPA1 (deprecated/insecure) |

## Virtualization Comparison
| Type | Isolation Level | Overhead | Example |
|---|---|---|---|
| VM (Type 1/2 hypervisor) | Full OS per instance | High | ESXi, Hyper-V |
| Container | Shares host kernel | Low | Docker |
| VRF | Network (L3) routing table isolation only | N/A (network construct) | Cisco VRF-Lite |

## MAC Address Table Behavior
- Switch learns **source MAC + ingress port** on every frame.
- Unknown destination MAC → **flood** out all ports except ingress (within VLAN).
- Known destination MAC → **forward** out the single learned port.
- Broadcast/multicast frames always flood.

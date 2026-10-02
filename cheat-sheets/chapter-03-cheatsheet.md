# Chapter 3 Cheat Sheet: VLANs, Trunking, Discovery Protocols

## VLAN Configuration Commands
| Task | Command |
|---|---|
| Create VLAN | `vlan 10` then `name SALES` |
| Assign access port | `switchport mode access` + `switchport access vlan 10` |
| Verify VLAN-to-port map | `show vlan brief` |

**Exam note:** `show vlan brief` only shows access ports — trunk ports never appear listed under a VLAN.

## Trunk Configuration Commands
| Task | Command |
|---|---|
| Set encapsulation (if supported) | `switchport trunk encapsulation dot1q` |
| Enable trunk mode | `switchport mode trunk` |
| Set native VLAN | `switchport trunk native vlan <id>` |
| Restrict allowed VLANs | `switchport trunk allowed vlan <list>` |
| Modify allowed list | `switchport trunk allowed vlan add/remove/except <list>` |
| Verify trunk state | `show interfaces trunk` |

**Exam note:** Default native VLAN = **VLAN 1**. Both trunk ends must match or CDP logs a native VLAN mismatch — untagged traffic leaks into the wrong VLAN, but the trunk stays up.

## 802.1Q Tagging
- 802.1Q inserts a 4-byte tag (12-bit VLAN ID field → 4094 usable VLAN IDs, 0 and 4095 reserved).
- **Native VLAN** traffic is sent **untagged**; all other VLANs are tagged.
- Normal VLAN range: **1–1005**. Extended range: **1006–4094**.

## CDP vs LLDP
| Feature | CDP | LLDP |
|---|---|---|
| Standard | Cisco-proprietary | IEEE 802.1AB (open) |
| Default advertise interval | 60 sec | 30 sec |
| Default holdtime | 180 sec | 120 sec (4x interval) |
| Multi-vendor support | No | Yes |
| Typical use | Cisco IP phone voice VLAN discovery | Multi-vendor topology mapping |

**Exam note:** Cisco IP Phones use CDP by default to learn voice VLAN; non-Cisco endpoints often require LLDP-MED.

## Verification Commands
| Command | Purpose |
|---|---|
| `show vlan brief` | Access port-to-VLAN mapping |
| `show interfaces trunk` | Trunk status, native VLAN, allowed VLANs |
| `show cdp neighbors detail` | Full neighbor info: IP, platform, capabilities |
| `show lldp neighbors detail` | LLDP equivalent, vendor-neutral |

## Common Exam Traps
1. Native VLAN mismatch → trunk stays **up**; only causes traffic leakage + a syslog/CDP warning, not link failure.
2. Trunk ports never show under `show vlan brief` — students wrongly assume a missing port entry means it's down.
3. Confusing CDP (Cisco-only, 60/180s timers) with LLDP (open standard, 30/120s timers) — the exam directly tests which protocol to pick for mixed-vendor gear.

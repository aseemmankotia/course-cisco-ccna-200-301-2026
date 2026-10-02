## Chapter 7 Cheat Sheet — FHRP & Route Selection

### FHRP Purpose
Provides transparent default-gateway failover using a shared **Virtual IP (VIP)**. Hosts keep one gateway IP/MAC even if the physical active router changes.

### FHRP Comparison
| Protocol | Vendor | Mode | Virtual MAC Format |
|---|---|---|---|
| HSRP | Cisco | Active/Standby | 0000.0C07.ACxx (v1) / 0000.0C9F.Fxxx (v2) |
| VRRP | Open standard | Master/Backup | 0000.5E00.01xx |
| GLBP | Cisco | Multi-active (AVG/AVF) | 0007.B400.xxyy |

### HSRP Election Rules
- Default priority = **100**; range 0–255; higher wins.
- Ties broken by highest configured/physical IP address.
- **preempt** required for a higher-priority router to reclaim active role after recovery — without it, the current active stays active even if less preferred.
- Multicast hellos: 224.0.0.2 (v1) / 224.0.0.102 (v2), UDP 1985.

### Key Commands
```
interface g0/0
 standby 1 ip 10.1.1.1
 standby 1 priority 150
 standby 1 preempt
 standby 1 authentication md5 key-string CCNA
```

### Administrative Distance (Lower = More Trusted)
| Source | AD |
|---|---|
| Connected | 0 |
| Static | 1 |
| eBGP | 20 |
| EIGRP (internal) | 90 |
| OSPF | 110 |
| RIP | 120 |
| EIGRP (external) | 170 |
| iBGP | 200 |
| Unknown/unreachable | 255 |

### Route Selection Order
1. **Longest prefix match wins** — always checked first, regardless of AD.
2. If prefixes are identical (same network+mask) from multiple sources → **lowest AD wins**.
3. If same source/protocol with equal metric → **load balance** (equal-cost).

### Gateway of Last Resort
- The next-hop of the default route (0.0.0.0/0).
- Displayed at top of `show ip route`.
- Used only when no more specific route matches.

### Common Exam Traps
- Priority set but no **preempt** → router does NOT reclaim active status.
- Assuming AD decides everything — **longest match always beats AD**.
- Believing HSRP/VRRP load-balance traffic — only **GLBP** does.
- Asymmetric routing from FHRP/static route mismatch breaking stateful firewalls/NAT.
- Confusing VRRP's priority 255 (IP address owner) with HSRP's default 100.

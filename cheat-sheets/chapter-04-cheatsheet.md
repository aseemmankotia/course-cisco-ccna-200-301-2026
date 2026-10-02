## Chapter 4 Cheat Sheet — EtherChannel, RSTP, WLC Basics
**Domain:** Network Access (20%)

### EtherChannel Negotiation Protocols
| Protocol | Standard | Modes | Forms Channel? |
|---|---|---|---|
| LACP | IEEE 802.3ad / 802.1AX | active + active | Yes |
| LACP | | active + passive | Yes |
| LACP | | passive + passive | **No** |
| PAgP | Cisco proprietary | desirable + desirable | Yes |
| PAgP | | desirable + auto | Yes |
| PAgP | | auto + auto | **No** |
| Static | none (no negotiation) | on + on | Yes (risk: mismatched config = loop/loss) |

**Limits:** Max 8 active links per bundle; LACP supports up to 16 total (8 active + 8 standby).

**Load-balance command:** `port-channel load-balance {src-mac | dst-mac | src-dst-mac | src-ip | dst-ip | src-dst-ip | src-dst-port}` (global config)

**Config commands:**
```
interface range Gi0/1-2
 channel-group 1 mode active
```

### Rapid PVST+ Root Bridge Election
Bridge ID = **Priority** (default 32768, step 4096) + **Extended System ID** (VLAN) + **MAC address**
Lowest Bridge ID wins. Tie on priority → lowest MAC wins.

Set priority: `spanning-tree vlan 10 priority 24576`
Macro: `spanning-tree vlan 10 root primary` (auto-lowers priority)

### Port Roles vs States
| Role | Meaning | Typical State |
|---|---|---|
| Root Port | Best path to root (1 per switch) | Forwarding |
| Designated Port | Best port per segment | Forwarding |
| Alternate Port | Backup path to root | Discarding |
| Backup Port | Backup on shared segment | Discarding |

**RSTP States (3):** Discarding → Learning → Forwarding
**Legacy STP States (5):** Blocking, Listening, Learning, Forwarding, Disabled

### PortFast & BPDU Guard
- `spanning-tree portfast` — interface, access ports only
- `spanning-tree bpduguard enable` — interface, err-disables on BPDU
- `spanning-tree portfast bpduguard default` — global, applies to all PortFast ports
- **Never** enable PortFast on trunk/switch-to-switch links

### WLC Basics
**Management access:** Console, HTTPS (GUI), SSH (CLI)
**Interfaces:** Management interface (in-band mgmt/AAA), Dynamic interfaces (mapped to VLANs for WLANs), Virtual interface (used for DHCP relay, web auth, mobility)

**WLAN creation order:** Create WLAN (SSID) → map to interface/VLAN → set Layer 2 security → enable WLAN

**Security comparison:**
| Type | Key Exchange | Notes |
|---|---|---|
| WPA2-Personal | PSK, 4-way handshake | Vulnerable to offline dictionary attack |
| WPA2-Enterprise | 802.1X/RADIUS | Per-user credentials |
| WPA3-Personal | SAE | Forward secrecy, resists offline attacks |

**QoS Profiles (high→low):** Platinum (voice) > Gold (video) > Silver (default, best effort) > Bronze (background)

### Exam Gotchas
1. Passive-passive LACP never forms a channel — commonly missed.
2. Root election tiebreaker order: Priority first, then MAC — not the reverse.
3. RSTP has 3 states, not 5 — don't confuse with legacy STP.

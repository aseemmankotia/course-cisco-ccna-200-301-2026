## Chapter 8 Cheat Sheet: NAT, NTP, DHCP/DNS, SNMP, Syslog, QoS

### NAT Types
| Type | Mapping | Command Example |
|---|---|---|
| Static | 1:1 permanent | `ip nat inside source static 10.1.1.1 203.0.113.1` |
| Dynamic Pool | Pool, 1:1 at a time | `ip nat pool P1 203.0.113.1 203.0.113.10 netmask 255.255.255.0` + `ip nat inside source list 1 pool P1` |
| PAT (Overload) | Many:1 (or few), port-based | `ip nat inside source list 1 interface Gi0/1 overload` |

Interfaces: `ip nat inside` / `ip nat outside` required on respective interfaces.
Verify: `show ip nat translations`, `show ip nat statistics`, `clear ip nat translation *`

### NTP
- Port: UDP 123
- Stratum 0 = reference clock (not a network device)
- Stratum 1 = directly attached to stratum 0
- Stratum 2-15 = increasing distance from source
- Stratum 16 = unsynchronized
- Commands: `ntp server <ip>`, `show ntp status`, `show ntp associations`

### DHCP (DORA) & Relay
- Discover → Offer → Request → Acknowledge (all broadcast by default)
- Relay: `ip helper-address <server-ip>` on client-facing SVI/interface
- Default forwarded UDP services include: DHCP (67/68), TFTP (69), DNS (53), TACACS (49), NetBIOS (137/138), Time (37)

### DNS Record Types
| Record | Purpose |
|---|---|
| A | Hostname → IPv4 |
| AAAA | Hostname → IPv6 |
| CNAME | Alias to another name |
| MX | Mail exchange server |
| NS | Authoritative name server |
| PTR | IP → hostname (reverse) |
| SOA | Zone authority info |

### SNMP
- Versions: v1, v2c (community string, plaintext), v3 (auth + encryption)
- GET (UDP 161) = manager polls agent
- TRAP (UDP 162) = agent pushes unsolicited alert
- Components: Manager, Agent, MIB

### Syslog Severity Levels (0=most severe)
| # | Level |
|---|---|
| 0 | Emergency |
| 1 | Alert |
| 2 | Critical |
| 3 | Error |
| 4 | Warning |
| 5 | Notice |
| 6 | Informational |
| 7 | Debugging |
Mnemonic: Every Awesome Cisco Engineer Will Need Icecream Daily

### QoS Concepts
| Term | Function |
|---|---|
| Classification | Identify traffic type |
| Marking | Tag traffic (DSCP/CoS) |
| Queuing | Manage packets during congestion |
| Policing | Drop/remark excess traffic immediately, no buffer |
| Shaping | Buffer/delay excess traffic to smooth rate |

### Remote Access & File Transfer
| Protocol | Port | Security |
|---|---|---|
| SSH | TCP 22 | Encrypted |
| Telnet | TCP 23 | Plaintext |
| TFTP | UDP 69 | No auth |
| FTP | TCP 20/21 | Auth supported |

### Common Exam Traps
- Forgetting `overload` keyword turns PAT into limited dynamic NAT (runs out of addresses).
- Confusing stratum 0 (reference clock) with stratum 1 (first network device).
- Reversing syslog severity order (0 = most severe, not least).
- Confusing policing (drops, no buffer) with shaping (buffers, delays).

# Chapter 5 Cheat Sheet: Routing Tables & Static Routing

## Administrative Distance (Exam-Critical Values)
| Source | AD |
|---|---|
| Connected | 0 |
| Static | 1 |
| EIGRP (internal) | 90 |
| OSPF | 110 |
| RIP | 120 |
| EIGRP (external) | 170 |
| Unknown/unreachable | 255 |

Lower AD = more trusted. AD is ONLY compared when two sources advertise the **exact same prefix and mask**.

## Route Selection Order (in priority)
1. **Longest prefix match** — most specific mask always wins, regardless of AD.
2. **Lowest Administrative Distance** — used only when prefixes are identical.
3. **Lowest metric** — used only when AD and protocol are the same (enables equal-cost load balancing).

## show ip route — Key Codes
| Code | Meaning |
|---|---|
| C | Directly connected |
| L | Local host route (/32 for router's own interface IP) |
| S | Static route |
| S* | Candidate default static route (0.0.0.0/0) |
| D | EIGRP |
| O | OSPF |
| R | RIP |

"Gateway of last resort" line = the currently active default route (any protocol flagged with *).

## Static Route Configuration
**IPv4 static:**
```
ip route <network> <mask> {next-hop-ip | exit-int} [AD]
```
**IPv4 default:**
```
ip route 0.0.0.0 0.0.0.0 <next-hop>
```
**IPv4 host route:**
```
ip route 10.10.10.5 255.255.255.255 <next-hop>
```
**IPv6 static:**
```
ipv6 route <prefix>/<len> {next-hop-ipv6 | exit-int}
```
**IPv6 default:**
```
ipv6 route ::/0 <next-hop>
```

## Floating Static Route (Backup Path)
Set AD higher than the primary route's AD:
```
ip route 10.0.0.0 255.0.0.0 192.168.2.1 170
```
Stays out of RIB while EIGRP/OSPF route is up; installed automatically if the primary route is withdrawn.

## Troubleshooting Missing/Wrong Routes
- Route missing entirely? Check if a **lower-AD source** to the exact same prefix is suppressing it (verify with `show ip route <prefix>` and check EIGRP/OSPF neighbor tables).
- Wrong path chosen? Check for a **more specific (longer prefix)** route stealing traffic — longest match always wins first.
- Static route not appearing? Confirm next-hop is **reachable/recursive** — IOS won't install a static route if it can't resolve the next-hop via another route.
- No mask accepted in CIDR form for `ip route` — must use dotted-decimal.
- Exit-interface static routes on multi-access networks may cause proxy-ARP issues — prefer next-hop IP on Ethernet.

## Chapter 7: First-Hop Redundancy and Route Selection Mastery — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | HSRP default priority value? | 100. Higher priority wins the active router election. Exam tip: without 'preempt', a recovered router with higher priority will NOT reclaim active status. |
| 2 | HSRPv1 virtual MAC address format? | 0000.0C07.ACxx, where xx is the HSRP group number in hex. Exam tip: HSRPv2 uses 0000.0C9F.Fxxx and supports group numbers up to 4095. |
| 3 | VRRP virtual MAC address format? | 0000.5E00.01xx, where xx is the VRRP group ID in hex. Exam tip: don't confuse this with HSRP's 0000.0C07.ACxx format. |
| 4 | HSRP vs VRRP vs GLBP — key exam difference? | HSRP (Cisco proprietary) and VRRP (open standard) are active/standby (one forwarder). GLBP (Cisco proprietary) allows multiple active forwarders for load balancing via AVG/AVF roles. |
| 5 | Command to make an HSRP router reclaim active role after recovering from failure? | standby [group] preempt. Exam tip: priority alone is not enough — preempt must also be configured on the router that should reclaim active status. |
| 6 | Command to set HSRP priority to 150 for group 1? | standby 1 priority 150. Exam tip: default priority is 100; higher value wins election. |
| 7 | Administrative Distance: Connected, Static, EIGRP (internal), OSPF, RIP? | Connected=0, Static=1, EIGRP internal=90, OSPF=110, RIP=120. Exam tip: lower AD = more trusted source; used only when comparing routes to the SAME prefix/mask. |
| 8 | What determines the installed route when two routes exist for the exact same prefix and mask from different sources? | The route from the source with the LOWEST administrative distance is installed. Exam tip: metric (e.g., OSPF cost) only matters within the same protocol, not across different sources. |
| 9 | What determines the installed route when routes exist for different prefix lengths covering an address? | Longest prefix match ALWAYS wins, regardless of administrative distance. Exam tip: AD is only a tiebreaker for identical prefix/mask, never overrides longest match. |
| 10 | What is 'Gateway of last resort' in show ip route output? | The next-hop of the default route (0.0.0.0/0), used only when no more specific route matches the destination. Exam tip: appears as a labeled line at the top of 'show ip route' output. |
| 11 | What causes asymmetric routing in an FHRP environment? | Misconfigured HSRP priority/preempt or inconsistent static/dynamic routes causing outbound and return traffic to traverse different gateways. Exam tip: dangerous with stateful firewalls/NAT — return traffic may get dropped due to missing session state. |
| 12 | Purpose of any FHRP (HSRP/VRRP/GLBP)? | Provides default gateway redundancy so hosts continue reaching the network if their configured gateway router fails, using a shared virtual IP (and virtual MAC) that fails over between physical routers. |

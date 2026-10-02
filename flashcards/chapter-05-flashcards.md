## Chapter 5: Routing Tables and IPv4/IPv6 Static Routing — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Administrative Distance: Directly Connected route | 0 — the most trusted source. Exam tip: a connected route to a prefix always wins over any static or dynamic route to that same prefix. |
| 2 | Administrative Distance: Static route (default) | 1 — trusted more than any dynamic routing protocol by default. Can be manually changed (1-255) to create a floating static route. |
| 3 | Administrative Distance: EIGRP (internal) | 90 — lower than OSPF and RIP, so EIGRP internal routes are preferred over them for the same prefix. |
| 4 | Administrative Distance: OSPF | 110 — higher (less trusted) than EIGRP internal (90), lower (more trusted) than RIP (120). |
| 5 | Administrative Distance: RIP | 120 — one of the least trusted IGPs on the exam. Beaten by static, EIGRP, and OSPF for the same prefix. |
| 6 | Administrative Distance: EIGRP (external) | 170 — much higher than EIGRP internal (90) because it represents routes redistributed from outside the EIGRP domain. |
| 7 | Administrative Distance: Unreachable/unknown source | 255 — the route is never installed or used; effectively means 'do not trust this source at all.' |
| 8 | Route selection order (three-step process) | 1) Longest prefix match (most specific /x wins) → 2) Lowest Administrative Distance (only if same exact prefix) → 3) Lowest metric (only if same protocol/AD, e.g., ECMP). Exam tip: AD never beats a longer prefix match. |
| 9 | What is a floating static route? | A static route configured with an AD higher than the primary route's AD (e.g., static AD 200 vs. EIGRP AD 90) so it acts as a backup path, only installed when the primary route disappears from the RIB. |
| 10 | IOS command: static IPv4 route syntax | ip route <network> <subnet-mask> {next-hop-ip \| exit-interface} [AD] Example: ip route 10.0.0.0 255.255.255.0 192.168.1.1 — mask must be dotted-decimal, not CIDR. |
| 11 | IOS command: IPv6 static route syntax | ipv6 route <prefix>/<prefix-length> {next-hop-ipv6 \| exit-interface} Example: ipv6 route 2001:db8:1::/64 2001:db8:2::1. Default route uses ::/0. |
| 12 | Host route configuration and purpose | ip route 10.10.10.5 255.255.255.255 <next-hop> Uses a /32 mask to match a single host exactly. Because it's the longest possible match, it's always preferred over any broader route to that same host. |

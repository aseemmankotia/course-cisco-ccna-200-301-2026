## Chapter 5: Routing Tables and IPv4/IPv6 Static Routing — Practice Questions

**Q1.** A router has two paths to reach 192.168.1.130: a route to 192.168.1.0/24 learned via EIGRP, and a static route to 192.168.1.128/25 configured by the administrator. Which route does the router install and use to forward a packet destined for 192.168.1.130?

A) The static route to 192.168.1.128/25, because it has the longest prefix match
B) The EIGRP route to 192.168.1.0/24, because EIGRP has a lower AD than static
C) Both routes are installed and load-balanced equally
D) Neither route is used; the packet is dropped due to a routing conflict

<details>
<summary>Answer</summary>

**Correct: A**

Longest prefix match is evaluated before AD or metric. /25 is more specific than /24, so it wins regardless of the fact that static has a higher numeric AD than EIGRP would in a direct tie.

**Why the others are wrong:**
- AD only decides between routes to the EXACT same prefix — it never overrides a longer (more specific) match.
- Routers do not load-balance across different prefix lengths; only equal-cost paths to the same prefix are balanced.
- There is no conflict — routers always prefer the most specific match; the packet is forwarded normally.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An administrator configures a backup path with 'ip route 10.0.0.0 255.0.0.0 192.168.2.1 170' while EIGRP (AD 90) is also advertising the same 10.0.0.0/8 network. What is this configuration called, and what happens under normal conditions?

A) A default route; it is used only when no other route exists
B) A floating static route; it stays in the RIB but is not used unless the EIGRP route disappears
C) A host route; it takes precedence over EIGRP immediately
D) An invalid configuration; static AD cannot be changed above 1

<details>
<summary>Answer</summary>

**Correct: B**

Setting a static route's AD higher than the primary dynamic route's AD (170 > 90) creates a floating static route. It remains in the routing table's candidate list but is only installed into the forwarding table if the EIGRP route is withdrawn.

**Why the others are wrong:**
- A default route uses network 0.0.0.0 0.0.0.0, not a specific prefix like 10.0.0.0/8.
- A host route uses a /32 mask; this is a /8 network, and floating logic wouldn't apply if it 'took precedence immediately'.
- Static route AD is fully configurable from 1-255 as the last parameter of the ip route command; 170 is valid.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A branch router shows no route to 172.16.50.0/24 in 'show ip route', but the neighboring router confirms the network is up and OSPF is advertising it. Which of the following is the MOST likely cause?

A) The OSPF process ID differs between routers
B) The router's OSPF neighbor adjacency is stuck in FULL state
C) The interface facing the OSPF neighbor is administratively up
D) OSPF's AD of 110 is being beaten by a competing static or connected route to the exact same prefix

<details>
<summary>Answer</summary>

**Correct: D**

If the exact same prefix is learned by two sources, the lower AD wins and is installed; the higher-AD route (OSPF, 110) is suppressed from the RIB entirely, explaining why it's completely missing rather than just unused.

**Why the others are wrong:**
- Mismatched process IDs are locally significant and don't prevent adjacency or route exchange between routers.
- A FULL adjacency state means OSPF is working correctly, not causing the problem.
- An interface being administratively up is the desired/normal state, not a fault.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which command correctly configures an IPv6 default route pointing to next-hop 2001:db8:1::1?

A) ip route 0.0.0.0 0.0.0.0 2001:db8:1::1
B) ipv6 route ::/0 2001:db8:1::1
C) ipv6 route 0.0.0.0/0 2001:db8:1::1
D) ipv6 default-route 2001:db8:1::1

<details>
<summary>Answer</summary>

**Correct: B**

IPv6 default routes use the prefix ::/0 (all zeros compressed), configured with 'ipv6 route ::/0 <next-hop-or-exit-interface>'.

**Why the others are wrong:**
- This is IPv4 syntax and uses an IPv6 address as next-hop — invalid mix.
- 0.0.0.0/0 is IPv4 dotted-decimal notation, not valid for the ipv6 route command.
- This command does not exist in Cisco IOS.

</details>

---

**Q5.** A network engineer needs to route traffic to a single troubleshooting host at 10.10.10.5 out a specific path without affecting the rest of the 10.10.10.0/24 subnet. Which route type should be configured?

A) A default route
B) A host route (10.10.10.5 255.255.255.255)
C) A floating static route
D) A summarized static route for 10.10.10.0/25

<details>
<summary>Answer</summary>

**Correct: B**

A host route uses a /32 mask (255.255.255.255), matching only that single IP address, and its longest-prefix-match status guarantees it's preferred over the broader /24 route for that one host.

**Why the others are wrong:**
- A default route (0.0.0.0/0) is a catch-all for unmatched traffic, the opposite of targeting one host.
- A floating static route relates to AD-based backup paths, not host-specific targeting.
- A /25 summary still covers 128 addresses, not a single host, and doesn't meet the requirement.

</details>

---

**Q6.** In 'show ip route' output, which code and symbol combination identifies the route currently acting as the Gateway of Last Resort?

A) C — indicates the connected default network
B) D — an EIGRP-learned default route only
C) S* — a static default route (0.0.0.0/0) installed in the routing table
D) L — a local host route used for the default gateway

<details>
<summary>Answer</summary>

**Correct: C**

S* specifically denotes a static route to 0.0.0.0/0 (or a candidate default flagged with the 'default' keyword), and this is what populates the 'Gateway of last resort' line at the top of the output.

**Why the others are wrong:**
- C simply marks any directly connected interface network, not specifically a default route.
- The Gateway of last resort can come from any protocol (S*, D*, O*E2, etc.) — 'D' alone without the asterisk doesn't denote default candidacy.
- L marks a local /32 route automatically created for the router's own interface IP, unrelated to default routing.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which command correctly configures a static IPv4 route to network 172.20.0.0/16 using next-hop IP 192.168.1.1?

A) ip route 172.20.0.0/16 192.168.1.1
B) route add 172.20.0.0 255.255.0.0 192.168.1.1
C) ip route 172.20.0.0 255.255.0.0 192.168.1.1
D) ip static-route 172.20.0.0 255.255.0.0 192.168.1.1

<details>
<summary>Answer</summary>

**Correct: C**

Cisco IOS static route syntax requires the network address and full subnet mask in dotted-decimal (not CIDR slash notation), followed by the next-hop IP or exit interface: ip route <network> <mask> <next-hop>.

**Why the others are wrong:**
- IOS 'ip route' does not accept CIDR slash notation for the mask.
- 'route add' is a Linux/Windows OS command syntax, not valid Cisco IOS.
- 'ip static-route' is not a valid IOS command; the correct keyword is simply 'ip route'.

</details>

---

**Q8.** A router has both an OSPF route (AD 110) and a RIP route (AD 120) learned for the exact same prefix, 203.0.113.0/24. Which route is installed in the routing table?

A) The RIP route, because RIP has a higher metric ceiling
B) Both routes are installed and equally load-balanced
C) The OSPF route, because it has the lower administrative distance
D) Neither; a conflict causes the route to be withdrawn

<details>
<summary>Answer</summary>

**Correct: C**

When two sources advertise the identical prefix and mask, the router prefers the source with the lower administrative distance. OSPF's AD of 110 beats RIP's AD of 120, so only the OSPF route is installed.

**Why the others are wrong:**
- RIP's metric (hop count) is irrelevant here since AD comparison happens first and RIP loses on AD alone.
- Equal-cost load balancing only occurs between routes of the same protocol/AD with equal metrics to the same prefix, not across different protocols with different AD.
- There's no conflict-driven withdrawal in Cisco IOS route selection; the tie is resolved deterministically by AD.

</details>

---


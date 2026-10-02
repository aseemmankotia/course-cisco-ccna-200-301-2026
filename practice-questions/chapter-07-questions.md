## Chapter 7: First-Hop Redundancy and Route Selection Mastery — Practice Questions

**Q1.** R1 and R2 run HSRP group 10. R1 has priority 150, R2 has default priority. R1 was active, then rebooted. Neither router has preempt configured. After R1 comes back online, which router is the HSRP active router for group 10?

A) R1, because it has the higher priority
B) Whichever router has the lower IP address on the SVI
C) Both routers, because HSRP load-balances by default
D) R2, because R1 does not reclaim active status without preempt

<details>
<summary>Answer</summary>

**Correct: D**

Without the 'standby X preempt' command, a router with higher priority will NOT take back the active role once another router has already become active — it stays standby even though its priority is higher.

**Why the others are wrong:**
- Priority only matters during the initial election or when preempt is configured; it does not force a takeover here.
- HSRP does not use IP address as a tiebreaker for active/standby role after the fact — priority (or router ID as tiebreaker) applies only during election.
- HSRP is active/standby only; GLBP is the protocol that load-balances across multiple gateways.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A router has the following routes to reach 10.10.10.0/24: a static route with AD 1, and an OSPF-learned route with AD 110, both for the exact same prefix and mask. Which route is installed in the routing table?

A) The OSPF route, because dynamic routing is always preferred for redundancy
B) Both routes are installed and load-balanced automatically
C) The static route, because it has the lower administrative distance
D) Neither route is installed until a floating static is configured

<details>
<summary>Answer</summary>

**Correct: C**

When two routing sources advertise the identical prefix and mask, the router picks the source with the lowest administrative distance. Static (AD 1) beats OSPF (AD 110).

**Why the others are wrong:**
- AD determines trustworthiness of the source, not routing protocol type; static beats OSPF by AD value regardless of 'dynamic vs static' reasoning.
- Equal-cost load balancing only happens between routes from the SAME source/protocol with equal metrics, not across different AD sources.
- A floating static (AD > the primary route's AD) is used for backup, not to make either route installable — this static already has AD 1, so it's the primary route.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A network engineer needs a first-hop redundancy solution where multiple routers in the group actively forward traffic simultaneously, load-balancing client traffic across all group members rather than using only one active router. Which protocol should be selected?

A) GLBP
B) HSRP
C) VRRP
D) STP

<details>
<summary>Answer</summary>

**Correct: A**

GLBP (Gateway Load Balancing Protocol) elects one AVG (Active Virtual Gateway) to assign different virtual MACs to multiple AVFs (Active Virtual Forwarders), allowing simultaneous load balancing across all group members.

**Why the others are wrong:**
- HSRP is Cisco-proprietary and active/standby only — a single router forwards traffic at a time per group.
- VRRP is the open-standard equivalent of HSRP and is also active/standby (called Master/Backup), not load-balancing.
- STP (Spanning Tree Protocol) prevents Layer 2 loops; it has nothing to do with default gateway redundancy.

</details>

---

**Q4.** Which command correctly configures a router to be the preferred HSRP active router for group 5 with priority 110 and reclaim active status when it comes back online?

A) standby 5 priority 110
B) standby 5 active 110 preempt
C) hsrp group 5 priority 110 preempt
D) standby 5 priority 110
standby 5 preempt

<details>
<summary>Answer</summary>

**Correct: D**

Both 'standby 5 priority 110' (sets higher priority) and 'standby 5 preempt' (allows the router to take back active role when it has higher priority) are required together to guarantee this router reclaims active status.

**Why the others are wrong:**
- Setting only priority without preempt means the router will win the initial election but will NOT reclaim active status after a failure/recovery.
- 'standby 5 active 110 preempt' is not valid HSRP syntax — 'active' is not a keyword used this way.
- 'hsrp' is not the correct command keyword on Cisco IOS; the keyword is 'standby' even though the protocol is called HSRP.

</details>

---

**Q5.** Two routers, R1 and R2, provide HSRP redundancy for a LAN segment behind a stateful firewall pair. R1 is HSRP active, but a misconfigured static route sends return traffic for some flows through R2 instead of R1. What is the most likely symptom of this misconfiguration?

A) Increased convergence time during HSRP failover only
B) Duplicate IP address errors on the LAN segment
C) Asymmetric routing causing the stateful firewall to drop return traffic
D) HSRP will automatically detect and correct the asymmetric path

<details>
<summary>Answer</summary>

**Correct: C**

When outbound and return traffic take different paths through different routers/firewalls, a stateful firewall on one path may not have session state for traffic returning via the other path, causing it to drop that traffic — the classic asymmetric routing problem.

**Why the others are wrong:**
- This is a routing/path selection issue, not a failover convergence issue.
- Duplicate IP errors relate to address conflicts, not to routing path asymmetry.
- HSRP only manages default gateway redundancy — it has no visibility into or control over the return path chosen by routing tables elsewhere in the network.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** What is the primary purpose of the HSRP virtual MAC address?

A) To uniquely identify each physical router interface on the LAN
B) To allow hosts to keep the same default gateway MAC address regardless of which physical router is currently active
C) To encrypt traffic between HSRP peers
D) To prevent Layer 2 loops on the redundant links

<details>
<summary>Answer</summary>

**Correct: B**

The virtual MAC (e.g., 0000.0C07.ACxx for HSRPv1) is mapped to the virtual IP; hosts ARP for and cache this MAC, so failover to a new active router is transparent — hosts never need to re-ARP.

**Why the others are wrong:**
- Each physical interface still keeps its own burned-in MAC; the virtual MAC is separate and shared conceptually by the group.
- HSRP has no encryption function; authentication (plain text or MD5) exists but is unrelated to the virtual MAC's purpose.
- Loop prevention is handled by STP, not HSRP virtual MACs.

</details>

---

**Q7.** A router has an OSPF route to 192.168.1.0/24 (AD 110) and a static route to 192.168.1.0/25 (AD 1) covering part of the same address space. A packet is destined for 192.168.1.10. Which route does the router use?

A) The OSPF route, because OSPF is generally more trusted for internal routing
B) The router load-balances between both routes
C) The static route, because /25 is a longer (more specific) prefix match
D) The static route, because static routes always win regardless of prefix length

<details>
<summary>Answer</summary>

**Correct: C**

Longest prefix match always takes precedence over administrative distance when routes for different prefix lengths exist. 192.168.1.10 falls within both, but /25 is more specific than /24, so it is chosen first — independent of AD.

**Why the others are wrong:**
- AD only decides between routes to the IDENTICAL prefix; it does not override longest match.
- Load balancing requires equal-cost paths to the same prefix/mask, which is not the case here.
- This answer describes the correct route but for the wrong reason — AD is irrelevant since the prefixes differ in length.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** In the output of 'show ip route', an engineer sees the line 'Gateway of last resort is 203.0.113.1 to network 0.0.0.0'. What does this indicate?

A) Traffic destined for networks not explicitly in the routing table will be forwarded to 203.0.113.1
B) The router has no default route configured and will drop all unmatched traffic
C) All traffic on the router is being forwarded through 203.0.113.1 regardless of destination
D) 203.0.113.1 is the HSRP virtual IP address for this segment

<details>
<summary>Answer</summary>

**Correct: A**

The gateway of last resort is simply the next-hop of the default route (0.0.0.0/0). It is used only when no more specific matching route exists in the routing table.

**Why the others are wrong:**
- The opposite is true — this line confirms a default route IS present and configured.
- Specific routes in the table still take precedence via longest match; the default route is used only as a last resort, not for all traffic.
- This line refers to Layer 3 routing table default route information, unrelated to any FHRP virtual IP configuration.

</details>

---


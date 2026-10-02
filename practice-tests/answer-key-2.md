# Answer Key — Practice Test 2

**Q1. Correct: B**

A /26 provides 2^6-2=62 usable host addresses, the smallest standard subnet size that satisfies the 50-host requirement, minimizing wasted addresses in a VLSM design.

---

**Q2. Correct: C**

Addresses beginning with the FE80::/10 prefix are link-local, auto-generated on every IPv6-enabled interface, used for on-link functions like neighbor discovery, and never routed beyond the local segment.

---

**Q3. Correct: A**

In the 2.4 GHz band, channels 1, 6, and 11 are the only non-overlapping 20 MHz channels in most regulatory domains, allowing adjacent APs to avoid co-channel and adjacent-channel interference.

---

**Q4. Correct: C**

UDP is connectionless with no handshake, acknowledgments, or retransmissions, resulting in lower latency and overhead — ideal for real-time voice/video where a late packet is worse than a dropped one.

---

**Q5. Correct: D**

In a spine-leaf design, every leaf switch connects to every spine switch, so traffic between any two leaf-attached servers always crosses exactly one spine — giving equal, predictable hop count and non-blocking east-west bandwidth.

---

**Q6. Correct: D**

VRF creates multiple independent routing tables on a single router, allowing overlapping IP address spaces between customers while keeping their routes and forwarding decisions completely isolated — a core technique in MPLS/VPN service provider networks.

---

**Q7. Correct: C**

/26 provides 64 total addresses (62 usable hosts), which is the smallest block that satisfies the 50-host requirement. This leaves enough of the remaining /24 address space to carve out the /27 (30 hosts), /28 (14 hosts), and /30 (2 hosts) subnets needed for B, C, and D. VLSM efficiency is tested heavily: always size each subnet to the smallest mask that fits the requirement, largest requirement first.

---

**Q8. Correct: C**

Unique Local Addresses use the FC00::/7 block; the locally-assigned range within it is FD00::/8, identified by a leading 'FD' as shown in FDA1:2B3C:4D5E:0001::1. ULAs function similarly to RFC 1918 private IPv4 addresses - routable inside an organization but not on the public internet. Exam tip: memorize FC00::/7 (and specifically FD00::/8) as the ULA range.

---

**Q9. Correct: C**

Single-mode fiber paired with 10GBASE-LR transceivers supports distances up to 10 km at 10 Gbps, comfortably covering the 2 km requirement. Exam note: single-mode fiber uses a laser light source and a narrow core, enabling much longer distances than multimode, and is the standard choice for inter-building or campus backbone links.

---

**Q10. Correct: B**

A native VLAN mismatch occurs when the two ends of an 802.1Q trunk disagree on which VLAN is untagged. This causes CDP/LLDP warnings and can leak traffic between VLANs. The fix is to make both sides agree on the same native VLAN, in this case setting SW2 back to native VLAN 1 to match SW1.

---

**Q11. Correct: A**

LACP requires at least one side to be in active mode to initiate negotiation. Active-active and active-passive combinations both successfully negotiate and form the EtherChannel, since one side actively sends LACP packets and the other side (passive) responds.

---

**Q12. Correct: A**

The root bridge is elected based on the lowest bridge ID, which is priority first, then MAC address only used as a tiebreaker when priorities are equal. SW2's priority of 24576 is lower than SW1 and SW3's 32768, so SW2 wins outright regardless of MAC address comparisons.

---

**Q13. Correct: A**

PortFast causes the port to skip the listening and learning STP states and go straight to forwarding on link up, and it also prevents the port from generating TCNs on normal link up/down events for end-host connections. BPDU Guard adds protection by immediately error-disabling the port if a BPDU is ever received, which happens if a switch is plugged in by mistake. Both together satisfy both requirements in the scenario.

---

**Q14. Correct: B**

LLDP (Link Layer Discovery Protocol) is defined by the IEEE 802.1AB standard and is supported across multiple vendors, making it useful in mixed environments. CDP (Cisco Discovery Protocol) is Cisco-proprietary and, in general, only Cisco devices participate in it, though CDP is still enabled by default on most Cisco platforms.

---

**Q15. Correct: B**

The management interface on a WLC is the primary interface used for in-band management access to the controller, including SSH, Telnet, SNMP, and the HTTPS web GUI, regardless of which subnet the administrator's device is on, as long as IP routing/reachability exists to that interface's IP.

---

**Q16. Correct: B**

LACP requires at least one side to be 'active' to initiate negotiation. Passive-passive never sends LACP packets first, so the channel never forms. Changing one side to active (active-active or active-passive both work) allows negotiation to succeed.

---

**Q17. Correct: A**

Root bridge election first compares bridge priority (lower wins). SW1 and SW2 tie at 4096, lower than SW3 (8192) and SW4 (32768). The tiebreaker between SW1 and SW2 is the lowest MAC address; 0011.1111.1111 is numerically lower than 0022.2222.2222, so SW1 wins.

---

**Q18. Correct: C**

CAPWAP uses UDP 5246 for the control plane (AP-to-WLC signaling, including join, configuration, and keepalives) and UDP 5247 for the data plane (encapsulated client traffic). The exam tests the exact control-port number.

---

**Q19. Correct: D**

The router always forwards based on the longest (most specific) matching prefix first, regardless of administrative distance or metric. Since 192.168.1.140 falls within all four routes, the router selects the /26 entry because it is the most specific match. AD and metric only break ties between routes to the identical prefix.

---

**Q20. Correct: C**

When multiple routing sources advertise the exact same destination prefix, the router installs only the route from the source with the lowest administrative distance. Static routes default to AD 1, which beats OSPF (110) and RIP (120).

---

**Q21. Correct: C**

A floating static route must have an administrative distance HIGHER than the primary route's AD so it stays in the background (in the RIB but unused) until the primary route is withdrawn. Since OSPF's AD is 110, an AD of 130 ensures the static route only becomes active if the OSPF route fails.

---

**Q22. Correct: A**

Because link-local IPv6 addresses are not globally routable and are only unique per interface, IOS requires that you specify BOTH the exit interface AND the link-local next-hop address when using a link-local address as the next hop for a static route. The correct syntax order is: prefix, exit-interface, next-hop.

---

**Q23. Correct: C**

The passive-interface command suppresses OSPF Hello packets on the specified interface only, preventing any neighbor adjacency from forming there — but the interface's connected network is still included in OSPF and advertised as a stub network to other routers.

---

**Q24. Correct: D**

The 'preempt' keyword allows a router to take over the active role from a lower-priority router at ANY time, not just during the initial election. Since R1 has both preempt enabled and a higher configured priority (150 > 100), it reclaims the active role as soon as it comes back online and its hello messages are received by R2.

---

**Q25. Correct: B**

When two different routing sources advertise the exact same prefix length, the router compares administrative distance first. EIGRP's default AD is 90, which is lower (more trusted) than OSPF's default AD of 110, so the EIGRP route is installed.

---

**Q26. Correct: B**

Assigning an administrative distance of 130 makes this static route less preferred than the OSPF route (AD 110). It only gets installed in the routing table — and used — if the OSPF-learned route is withdrawn, which is exactly how a floating static route is meant to function.

---

**Q27. Correct: D**

The longest prefix match rule is always applied first, before administrative distance or metric are ever considered. Since 10.1.1.0/24 is the most specific route that matches the destination 10.1.1.5, it is selected regardless of its source's AD value of 120.

---

**Q28. Correct: A**

The OSPF router-id selection order is: (1) manually configured router-id, (2) highest IP address among up loopback interfaces, (3) highest IP address among up physical interfaces. Loopback interfaces always outrank physical interfaces regardless of the actual IP value, so 1.1.1.1 is selected even though 10.0.0.2 is numerically higher.

---

**Q29. Correct: D**

Cisco HSRP assigns a default priority of 100 to all group members, and preemption is disabled by default. This means that if the original active router fails and later recovers, it will remain in standby state rather than automatically reclaiming the active role — 'standby preempt' must be explicitly configured for that behavior.

---

**Q30. Correct: D**

Adding 'overload' enables PAT (NAT overload), allowing all 50 hosts to share the 4 public addresses simultaneously by multiplexing on port numbers.

---

**Q31. Correct: D**

NTP stratum increases by one at each hop away from the reference clock. The router synced from a stratum 2 source becomes stratum 3 for anything synchronizing from it.

---

**Q32. Correct: B**

The 'ip helper-address' command configured on the client-facing SVI is required to relay DHCP broadcast requests as unicast to the specified DHCP server across VLANs/subnets.

---

**Q33. Correct: A**

'logging trap errors' sets the trap level to severity 3, which includes levels 0-3 (Emergencies, Alerts, Critical, Errors) and suppresses Warning (4) and lower severities.

---

**Q34. Correct: D**

Traffic policing monitors traffic rate and drops (or remarks) packets that exceed the configured rate immediately, without buffering, which matches the strict enforcement requirement described.

---

**Q35. Correct: A**

DHCP snooping builds a binding table of legitimate IP-to-MAC-to-port mappings by trusting only the uplink toward the real DHCP server. Dynamic ARP Inspection then uses that same binding table to validate ARP replies on untrusted (access) ports, blocking both rogue DHCP offers and spoofed ARP traffic.

---

**Q36. Correct: A**

The 'restrict' violation mode drops traffic from any MAC address that exceeds the configured maximum, increments the violation counter, and generates a syslog/SNMP message, but it does not disable the interface — the port stays operational for the already-learned address.

---

**Q37. Correct: C**

TACACS+ separates the AAA functions and encrypts the entire packet body, and critically it supports per-command authorization — allowing granular control such as permitting 'show' commands to one group while restricting 'configure terminal' to another, with full command-level accounting.

---

**Q38. Correct: B**

An extended numbered ACL can match both source and destination for any protocol. Using 'host' notation on both source and destination precisely targets only 10.10.20.55 talking to 172.16.5.10, and a trailing permit ip any any preserves all other traffic. Extended ACLs should be applied inbound as close to the source as possible for efficiency.

---

**Q39. Correct: A**

WPA3-Personal replaces the WPA2 4-way handshake with SAE (Simultaneous Authentication of Equals, based on Dragonfly key exchange), which provides forward secrecy and resists offline dictionary/brute-force attacks against captured handshake traffic — a well-known weakness of WPA2-PSK's 4-way handshake.

---

**Q40. Correct: D**

GRE supports multicast and broadcast traffic, which OSPF requires to form adjacencies (multicast to 224.0.0.5/224.0.0.6). Wrapping the GRE tunnel inside IPsec (GRE over IPsec) provides the needed encryption while still allowing OSPF to run over the GRE interface, satisfying both the security and dynamic-routing requirements.

---

**Q41. Correct: D**

DAI intercepts ARP packets on untrusted ports and validates the sender's IP-to-MAC mapping against the DHCP snooping binding table built from DHCP transactions. A host with a static IP never generated a DHCP transaction, so no binding exists, and DAI drops its ARP requests/replies as invalid. The correct fix is to configure a static ARP ACL for that host (or trust the port) and permit it in the DAI configuration.

---

**Q42. Correct: B**

Ansible is agentless and push-based — it connects to managed devices over SSH (or an API) from a control node and applies configuration on demand, with no persistent agent required on the target devices, matching this scenario exactly.

---

**Q43. Correct: C**

PATCH is designed for partial modification of an existing resource — it updates only the specified fields (the VLAN name) without requiring the full resource representation to be resent, which is exactly what the scenario calls for.

---

**Q44. Correct: B**

The northbound API is the interface exposed by the controller (Cisco DNA Center) toward applications and orchestration tools above it, allowing external software to request services, policies, and automation tasks programmatically.

---

**Q45. Correct: A**

The value of "management" is enclosed in curly braces { } and contains its own set of key-value pairs ("ip" and "enabled"), which makes it a nested JSON object (equivalent to a dictionary), not a simple scalar or array value.

---

**Q46. Correct: B**

Controller-based architectures centralize control-plane intelligence on the controller, which computes and pushes policy/configuration to devices via southbound protocols, allowing administrators to manage the network as a whole rather than configuring each device's control plane individually via CLI.

---


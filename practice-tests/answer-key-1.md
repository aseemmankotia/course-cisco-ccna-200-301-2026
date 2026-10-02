# Answer Key — Practice Test 1

**Q1. Correct: C**

A /27 mask provides 5 host bits (2^5 - 2 = 30 usable addresses), exactly matching the requirement with the least wasted space.

---

**Q2. Correct: B**

FE80::/10 is the link-local address range, automatically configured on every interface and required for protocols like Neighbor Discovery Protocol; it is never forwarded by routers.

---

**Q3. Correct: C**

UDP is connectionless with no retransmission or handshake overhead, making it ideal for latency-sensitive real-time traffic like voice where occasional packet loss is tolerable.

---

**Q4. Correct: B**

Single-mode fiber uses a laser light source and a narrow core, supporting distances well beyond 10 km, making it the only option that reliably covers an 8 km span.

---

**Q5. Correct: B**

A switch handles unknown unicast frames by flooding them out every port in the same VLAN except the port on which the frame arrived, ensuring the frame reaches the destination so the switch can learn its location from the reply.

---

**Q6. Correct: D**

In the 2.4 GHz band, channels 1, 6, and 11 are the only three channels that do not overlap with each other, making them the standard choice for multi-AP deployments to avoid interference.

---

**Q7. Correct: A**

A /25 subnet provides 2^7-2 = 126 usable host addresses, the smallest block that can accommodate 100 hosts. VLSM best practice is to allocate the largest subnet first from the available block, then subdivide the remainder for smaller subnets.

---

**Q8. Correct: A**

Link-local addresses (FE80::/10) are automatically generated on every IPv6 interface via EUI-64 or a random interface ID, and routers never forward packets sourced from or destined to a link-local address beyond the local segment.

---

**Q9. Correct: B**

Single-mode fiber (OS2) uses a single light path and supports 10 Gbps links (10GBASE-LR) over distances of up to 10 km or more, making it the only option that meets both the distance and bandwidth requirements.

---

**Q10. Correct: C**

An end-user host needs an access port, not a trunk. 'switchport mode access' combined with 'switchport access vlan 20' assigns the port to VLAN 20 untagged, which is exactly what a single-host connection requires.

---

**Q11. Correct: A**

A native VLAN mismatch occurs when each end of an 802.1Q trunk treats a different VLAN as untagged. Matching the native VLAN on both ends eliminates the mismatch and restores correct forwarding of untagged frames.

---

**Q12. Correct: C**

CDP is a Cisco-proprietary Layer 2 discovery protocol that only works between Cisco devices. LLDP (IEEE 802.1AB) is an open standard, so it works across different vendors' equipment, making it useful in mixed environments.

---

**Q13. Correct: B**

LACP (IEEE 802.3ad) is the standards-based EtherChannel negotiation protocol. 'active' mode causes the port to actively send LACP negotiation packets, and having both ends in active (or one active/one passive) mode forms the channel.

---

**Q14. Correct: C**

The 'spanning-tree vlan 10 root primary' macro automatically lowers SW2's bridge priority for VLAN 10 just enough to become root for that VLAN, without manually altering priorities on other switches or affecting other VLANs.

---

**Q15. Correct: C**

WPA3-Personal replaces the PSK exchange used in WPA2 with SAE, which resists offline dictionary attacks and provides forward secrecy, making it the strongest of the listed options for this requirement.

---

**Q16. Correct: B**

SW1 is running LACP (mode active), the IEEE 802.3ad standard protocol. Changing SW2 to 'passive' keeps it on LACP and negotiates successfully with SW1's active side, satisfying both the technical requirement and the IEEE-standard policy.

---

**Q17. Correct: D**

Bridge priority must be a multiple of 4096 in the range 0-61440. Setting it explicitly to 0 directly assigns the lowest possible usable value, guaranteeing this switch wins root bridge election for VLAN 10 over any other switch with a higher priority.

---

**Q18. Correct: A**

WPA3-Enterprise uses 802.1X with a RADIUS server for individual per-user authentication and adds 192-bit minimum-strength cryptography (AES-256-GCM), exceeding WPA2's encryption strength, satisfying both the unique-credential and stronger-encryption requirements.

---

**Q19. Correct: A**

When multiple sources advertise a route to the same destination, the router selects the route with the lowest administrative distance. A static route defaults to AD 1, which beats EIGRP (90) and OSPF (110), so it is installed regardless of metric.

---

**Q20. Correct: D**

By default, Cisco IOS routers use the longest match (most specific prefix) rule to forward packets. The /24 route is the most specific match for 10.1.1.50, so the router forwards via 192.168.2.1 even though the /16 and /8 routes also technically match.

---

**Q21. Correct: D**

A floating static route must have an administrative distance HIGHER than the AD of the primary route so it is only used when the primary route is unavailable. Since OSPF's AD is 110, specifying an AD of 115 on the static route ensures OSPF is preferred while the route is up, and the static route takes over only if OSPF fails.

---

**Q22. Correct: B**

IPv6 static routes use the 'ipv6 route' command with the destination prefix expressed in IPv6 notation. The IPv6 default route is written as ::/0, so the correct syntax is 'ipv6 route ::/0 GigabitEthernet0/1 2001:DB8::1'.

---

**Q23. Correct: A**

OSPF requires that the area ID configured on both ends of a shared link match exactly. Hello packets include the area ID, and a router will discard hello packets received with a mismatched area ID, so R1 and R2 never even become neighbors — they don't even reach the 2-way state.

---

**Q24. Correct: C**

HSRP's purpose is to provide first-hop gateway redundancy by having a standby router take over the shared virtual IP and virtual MAC address when the active router fails. Because hosts continue to send traffic to the same virtual IP/MAC, no host reconfiguration or ARP relearning is needed, and failover happens transparently and quickly.

---

**Q25. Correct: C**

A floating static route must have an administrative distance higher than the AD of the primary route (90). Setting AD 95 ensures the router only installs this static route in the RIB when the EIGRP route is withdrawn, correctly implementing backup behavior via the 'longest match, then AD' selection process.

---

**Q26. Correct: D**

The manually configured 'router-id x.x.x.x' command under 'router ospf' takes highest precedence in Router ID selection, overriding both loopback and physical interface IP addresses, and it does not change due to interface state or future interface additions — this is the only method that guarantees a stable, predictable ID.

---

**Q27. Correct: C**

HSRP (Hot Standby Router Protocol) is a First Hop Redundancy Protocol that creates a shared virtual IP and virtual MAC address across two or more routers. Hosts use the virtual IP as their default gateway; if the active router fails, the standby router takes over the virtual IP transparently, requiring zero host reconfiguration.

---

**Q28. Correct: A**

A host static route uses a /32 (255.255.255.255) mask to match only the single IP address 192.168.5.10. Because the router uses longest-match forwarding logic, this /32 route is always preferred over the broader /24 route for traffic to that one host, while all other hosts in the subnet continue to use the existing route.

---

**Q29. Correct: D**

The 'passive-interface' command suppresses OSPF Hello packets on the specified interface, which prevents any neighbor adjacency from forming over that interface. However, as long as the interface is included in a network statement under the OSPF process, its connected subnet is still advertised in OSPF LSAs to other routers — this is commonly used on LAN-facing interfaces where no OSPF neighbors are expected.

---

**Q30. Correct: B**

Using 'ip nat inside source list 1 interface GigabitEthernet0/1 overload' performs PAT (NAT overload) using the IP address already configured on the outside interface, allowing all hosts matched by ACL 1 to share that single public address via unique port mappings — exactly what the requirement calls for.

---

**Q31. Correct: C**

NTP stratum defines distance from the reference clock: stratum 0 devices are the reference clocks themselves (not directly polled over the network), stratum 1 servers are directly attached to them, and each subsequent hop increases the stratum number by one, up to a maximum of 15.

---

**Q32. Correct: D**

The 'ip helper-address' command configured on the client-facing interface (VLAN 10 SVI) converts DHCP broadcasts to a unicast and forwards them to the specified DHCP server address, enabling DHCP relay across subnets — this is the standard Cisco DHCP relay configuration.

---

**Q33. Correct: D**

Syslog severity levels are: 0-Emergency, 1-Alert, 2-Critical, 3-Error, 4-Warning, 5-Notice, 6-Informational, 7-Debug. 'Alert' is level 1, indicating action must be taken immediately, one step less severe than Emergency.

---

**Q34. Correct: A**

Traffic policing monitors traffic against a defined rate and immediately drops or remarks packets that exceed it, without buffering — making it ideal for enforcing strict bandwidth contracts at ingress interfaces.

---

**Q35. Correct: D**

The restrict violation mode drops traffic from the unauthorized MAC address, increments the violation counter, and generates a syslog message and SNMP trap, while leaving the interface operational.

---

**Q36. Correct: A**

DHCP snooping classifies switch ports as trusted or untrusted and blocks DHCP server responses (OFFER/ACK) arriving on untrusted ports, directly preventing rogue DHCP servers from serving clients.

---

**Q37. Correct: D**

In an extended ACL, the syntax is 'deny tcp <source> <destination> eq <port>'. This statement correctly denies TCP port 23 (Telnet) from source 10.1.1.10 to destination 10.1.1.100, followed by a permit for everything else.

---

**Q38. Correct: B**

DAI intercepts all ARP packets on untrusted ports and validates the IP-to-MAC bindings against the DHCP snooping binding table, dropping ARP packets with invalid or spoofed mappings.

---

**Q39. Correct: B**

WPA3-Personal replaces the WPA2 PSK four-way handshake with SAE (Dragonfly handshake), which protects against offline dictionary/brute-force attacks even if an attacker captures the handshake, addressing the known WPA2 KRACK-related weaknesses.

---

**Q40. Correct: D**

TACACS+ encrypts the entire packet body (not just the password), separates authentication, authorization, and accounting, and supports granular per-command authorization — making it the standard choice for device administration AAA.

---

**Q41. Correct: C**

DHCP snooping filters DHCP messages on untrusted ports, blocking DHCP server responses (OFFER/ACK) from unauthorized devices while allowing only trusted uplink ports to source them, directly preventing rogue DHCP servers.

---

**Q42. Correct: A**

Cisco DNA Center provides centralized, controller-based management that lets an engineer define and push consistent configuration policies (like VLANs) to many devices at once through northbound APIs and templates, eliminating per-device CLI work.

---

**Q43. Correct: B**

The value of "vlans" is enclosed in square brackets [10, 20, 30], which is JSON syntax for an array containing three numeric elements.

---

**Q44. Correct: A**

In REST APIs, POST corresponds to the Create operation in CRUD, and is used to submit new data to be created as a resource on the server, such as a new VLAN entry.

---

**Q45. Correct: A**

Valid JSON requires an object to be enclosed in curly braces with both the key and string value wrapped in double quotes, exactly as shown in {"hostname": "Router1"}.

---

**Q46. Correct: B**

The underlay is the physical infrastructure (switches, routers, and links) providing basic IP reachability, while the overlay is a logical network built on top of the underlay using tunneling protocols like VXLAN to carry traffic between endpoints.

---


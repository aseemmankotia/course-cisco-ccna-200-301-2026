## Chapter 6: Single-Area OSPFv2 Configuration and Verification — Practice Questions

**Q1.** Two routers connected via a shared Ethernet segment are configured for OSPF in the same area. Router A becomes the DR, Router B becomes a DROTHER. Show ip ospf neighbor on Router B shows a third router, Router C (also a DROTHER), stuck permanently in the 2-WAY state. What is the most likely explanation?

A) This is expected behavior — two DROTHER routers on a broadcast segment remain in 2-WAY with each other and only reach FULL with the DR and BDR
B) Router C has a mismatched hello/dead timer with Router B
C) Router C has a different OSPF area ID than Router B
D) Router C's MTU does not match Router B's MTU

<details>
<summary>Answer</summary>

**Correct: A**

On broadcast (and NBMA) network types, DROTHER routers only build full adjacencies with the DR and BDR to reduce LSA flooding overhead. Two DROTHERs correctly stay at 2-WAY with each other — this is normal, not a fault.

**Why the others are wrong:**
- A timer mismatch would prevent even 2-WAY from forming (neighbor would drop entirely, not stabilize)
- A mismatched area ID would prevent the neighbor from appearing at all, not stop it at 2-WAY
- An MTU mismatch causes a stall in EXSTART/EXCHANGE, not a stable 2-WAY state

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** Two directly connected routers running OSPF are stuck cycling between EXSTART and EXCHANGE and never reach FULL. Interfaces, area, subnet, and timers all match. What should you check next?

A) Router ID conflict between the two routers
B) Passive-interface configured on one of the interfaces
C) Interface MTU mismatch between the two routers
D) Wildcard mask used in the network statement

<details>
<summary>Answer</summary>

**Correct: C**

MTU mismatch is the classic cause of routers stalling in EXSTART/EXCHANGE: the larger-MTU router sends a Database Description packet the smaller-MTU router discards because it exceeds its configured MTU, so the exchange never completes.

**Why the others are wrong:**
- A duplicate Router ID prevents the neighbor relationship from forming at all (or causes flapping), not a stall specifically in EXSTART/EXCHANGE
- A passive interface would prevent hellos entirely, so the neighbor would never appear even in INIT
- Wildcard mask errors affect which interfaces run OSPF, not the state machine progression of an already-forming adjacency

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** R1 (area 0, hello 10, dead 40) and R2 (area 0, hello 5, dead 20) are on the same /30 subnet with OSPF enabled on both interfaces. What is the result?

A) They form a full adjacency because both use the default dead-to-hello ratio of 4:1
B) They form a full adjacency but exchange hellos at two different intervals
C) They never form an adjacency because hello and dead intervals must match exactly between neighbors
D) They form an adjacency but remain stuck in the INIT state indefinitely

<details>
<summary>Answer</summary>

**Correct: C**

Hello and dead intervals are among OSPF's mandatory adjacency-matching parameters (with area ID, subnet, and area type). A mismatch on either value blocks the neighbor from ever progressing past DOWN.

**Why the others are wrong:**
- The 4:1 ratio being consistent on each router individually doesn't matter — the exact values must match between the two routers
- OSPF does not tolerate asymmetric timers; it is not a negotiated parameter like MTU flooding order
- It won't even reach INIT — the neighbor relationship fails to establish at all when timers mismatch

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A router has Loopback0 (1.1.1.1), Loopback1 (2.2.2.2), and GigabitEthernet0/0 (10.0.0.1) all up when the OSPF process starts. No router-id command is configured. What Router ID does OSPF select?

A) 10.0.0.1, the highest active physical interface IP
B) 1.1.1.1, because Loopback0 is always preferred by name
C) A randomly generated 32-bit value since no loopback naming priority exists
D) 2.2.2.2, the highest IP address among all up loopback interfaces

<details>
<summary>Answer</summary>

**Correct: D**

Without a manually configured router-id, OSPF selects the highest IP address among up loopback interfaces first, regardless of loopback number. Only if no loopbacks exist does it fall back to the highest active physical interface IP.

**Why the others are wrong:**
- Physical interfaces are only used when no loopback interfaces are configured
- Loopback0 has no special naming priority — OSPF compares IP address values, not interface numbers
- OSPF never generates a random ID; the algorithm is deterministic

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A network engineer wants to eliminate DR/BDR election overhead on a point-to-point WAN link between two routers to speed up convergence. Which OSPF network type should be configured on both ends?

A) broadcast
B) point-to-point
C) point-to-multipoint
D) non-broadcast

<details>
<summary>Answer</summary>

**Correct: B**

The point-to-point network type disables DR/BDR election entirely (only two routers can ever exist on the link), forms adjacencies immediately using multicast hellos, and is the default type on serial interfaces with HDLC/PPP encapsulation.

**Why the others are wrong:**
- Broadcast network type still elects a DR/BDR, adding unnecessary overhead on a two-router link
- Point-to-multipoint is designed for hub-and-spoke NBMA topologies with more than two routers, not a simple point-to-point link
- Non-broadcast (NBMA) requires manual neighbor statements and also elects a DR/BDR, which is the opposite of the goal

</details>

---

**Q6.** You need to enable OSPF area 0 on exactly the interface with IP address 192.168.10.1/24 and no others. Which network statement under router ospf 1 achieves this?

A) network 192.168.10.0 0.0.0.255 area 0
B) network 192.168.10.1 255.255.255.0 area 0
C) network 192.168.10.0 255.255.255.0 area 0
D) network 192.168.10.1 0.0.0.0 area 0

<details>
<summary>Answer</summary>

**Correct: A**

OSPF network statements require a wildcard mask (inverse of a subnet mask), not a standard subnet mask. 0.0.0.255 matches any host within the 192.168.10.0/24 network, correctly enabling OSPF on that /24 interface.

**Why the others are wrong:**
- 255.255.255.0 is a standard subnet mask, not a wildcard mask — OSPF network statements reject this syntax or misinterpret it
- Using a standard mask (255.255.255.0) instead of a wildcard mask is invalid syntax for the network command
- 0.0.0.0 as a wildcard only matches the single exact host 192.168.10.1, which would fail to match the interface's network address entry as intended for the /24

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A branch router runs OSPF on GigabitEthernet0/1 (LAN, 50 hosts) and Serial0/0/0 (WAN uplink). The engineer wants the LAN subnet advertised in OSPF but does not want the router to send hello packets on the LAN interface to reduce unnecessary traffic and prevent rogue neighbor adjacencies. Which configuration accomplishes this?

A) router ospf 1 / passive-interface GigabitEthernet0/1
B) router ospf 1 / no network 192.168.1.0 0.0.0.255 area 0
C) interface GigabitEthernet0/1 / ip ospf priority 0
D) interface GigabitEthernet0/1 / shutdown

<details>
<summary>Answer</summary>

**Correct: A**

passive-interface suppresses OSPF hello packets on the specified interface while still including its connected subnet in the LSDB, exactly meeting both requirements: advertise the subnet, stop sending hellos.

**Why the others are wrong:**
- Removing the network statement stops advertising the subnet entirely, failing the requirement to keep it in OSPF
- ip ospf priority 0 only prevents the router from becoming DR/BDR — it still sends hellos and can form adjacencies
- Shutting down the interface takes the LAN offline completely, which is not the goal

</details>

---

**Q8.** Which OSPF neighbor state indicates that the master/slave relationship has been established and routers are actively exchanging Database Description (DBD) packets describing their link-state databases?

A) Exchange
B) 2-WAY
C) ExStart
D) Loading

<details>
<summary>Answer</summary>

**Correct: A**

In the Exchange state, routers actively send DBD packets summarizing their LSDB contents; the master/slave roles and initial sequence number were already decided during the preceding ExStart state.

**Why the others are wrong:**
- 2-WAY only confirms bidirectional hello communication; no DBD exchange has begun
- ExStart is where master/slave election and sequence numbers are negotiated, before any DBD content is exchanged
- Loading follows Exchange and involves sending Link-State Request/Update packets to fill in missing LSAs, not the DBD summary exchange

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---


## Chapter 6: Single-Area OSPFv2 Configuration and Verification — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | OSPFv2 neighbor states in order from Down to Full? | Down → Attempt (NBMA only) → Init → 2-Way → ExStart → Exchange → Loading → Full. Exam tip: DROTHER-to-DROTHER stops at 2-Way — that's normal, not a failure. |
| 2 | What four parameters MUST match for two OSPF routers to become neighbors at all? | Area ID, subnet/mask, hello interval, dead interval (also area type/stub flags and authentication). Mismatch = stuck in Down or neighbor never appears. MTU mismatch does NOT block neighbor forming — it stalls ExStart/Exchange instead. |
| 3 | Default OSPF hello and dead timers on broadcast/point-to-point networks? | Hello = 10 sec, Dead = 40 sec (4x hello). Exam tip: NBMA networks default to Hello = 30 sec, Dead = 120 sec. |
| 4 | OSPF Router ID selection order (no manual override)? | 1) Manually configured router-id (highest priority) 2) Highest IP among up loopback interfaces 3) Highest IP among up active physical interfaces. Exam tip: loopbacks don't need OSPF enabled on them to count toward RID selection. |
| 5 | Command to manually set OSPF Router ID? | router ospf 1\n router-id 1.1.1.1\nThen: clear ip ospf process to apply immediately (or reload). Exam tip: RID is chosen ONCE at process startup and doesn't change dynamically unless cleared. |
| 6 | OSPF network type: broadcast vs point-to-point — key difference? | Broadcast (default on Ethernet) elects a DR/BDR and uses multicast hellos to 224.0.0.5/6. Point-to-point (default on serial HDLC/PPP) has NO DR/BDR election — faster adjacency, only 2 routers possible. |
| 7 | Command syntax to enable OSPF on an interface using the network statement method? | router ospf 1\n network 10.1.1.0 0.0.0.255 area 0\nExam tip: the third field is a WILDCARD mask (inverse), not a subnet mask. |
| 8 | What does passive-interface do in OSPF? | Suppresses OSPF hello packets on the specified interface so no adjacency can form there, but the interface's connected subnet is still advertised (if covered by a network statement). Used on LAN-facing ports to prevent rogue neighbors. |
| 9 | Command to view OSPF neighbor table and states? | show ip ospf neighbor\nColumns: Neighbor ID, Pri, State (e.g., FULL/DR, 2WAY/DROTHER), Dead Time, Address, Interface. |
| 10 | Command to view OSPF process config including network statements and passive interfaces? | show ip protocols\nShows: Router ID, networks/areas configured, passive interface list, timers, and administrative distance. |
| 11 | Two OSPF routers stuck in ExStart/Exchange forever — most common cause? | MTU mismatch between the two interfaces. Fix: match ip mtu on both sides, or use 'ip ospf mtu-ignore' to bypass the check (not best practice for production). |
| 12 | Why do two DROTHER routers on the same broadcast segment stay at 2-Way with each other? | OSPF only forms full adjacencies between DROTHERs and the DR/BDR to limit LSA flooding traffic on multi-access segments. DROTHER-to-DROTHER 2-Way is expected, not a misconfiguration. |

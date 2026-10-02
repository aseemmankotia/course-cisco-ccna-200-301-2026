## Chapter 6: Single-Area OSPFv2 — Cheat Sheet

### Neighbor State Machine
| State | Meaning |
|---|---|
| Down | No hellos received |
| Attempt | NBMA only — manually configured neighbor, no hello yet |
| Init | Hello received, own RID not seen in it |
| 2-Way | Bidirectional hello confirmed; DR/BDR election happens here |
| ExStart | Master/slave role + initial DBD sequence number negotiated |
| Exchange | DBD packets exchanged (LSA headers only) |
| Loading | LSRs/LSUs sent to fill missing LSA details |
| Full | Databases fully synchronized — final state for adjacent neighbors |

**Exam trap:** DROTHER↔DROTHER stays at 2-Way permanently — that's correct behavior, not a fault.

### Mandatory Adjacency-Matching Parameters
| Parameter | Must Match? |
|---|---|
| Area ID | Yes |
| Subnet/Mask | Yes |
| Hello Interval | Yes |
| Dead Interval | Yes |
| Area type (stub flags) | Yes |
| Authentication | Yes (if configured) |
| MTU | Not required to form neighbor, but mismatch stalls ExStart/Exchange |

### Default Timers
| Network Type | Hello | Dead |
|---|---|---|
| Broadcast / Point-to-Point | 10s | 40s |
| NBMA | 30s | 120s |

### Router ID Selection Order
1. Manual `router-id x.x.x.x`
2. Highest IP on an **up** loopback interface
3. Highest IP on an **up** active physical interface

Apply manual RID change: `clear ip ospf process`

### Network Types
| Type | DR/BDR Election | Default On |
|---|---|---|
| Broadcast | Yes | Ethernet |
| Point-to-Point | No | Serial (HDLC/PPP) |
| Point-to-Multipoint | No | Manual config only |
| Non-Broadcast (NBMA) | Yes | Frame Relay (legacy) |

### Key Commands
```
router ospf 1
 router-id 1.1.1.1
 network 10.1.1.0 0.0.0.255 area 0
 passive-interface GigabitEthernet0/1

show ip ospf neighbor
show ip protocols
show ip ospf interface brief
clear ip ospf process
```

### Common Wrong Answers
- Confusing standard mask with wildcard mask in `network` statements.
- Assuming passive-interface removes the subnet from OSPF — it does NOT, only hellos are suppressed.
- Assuming 2-Way between DROTHERs is a failure.
- Assuming MTU mismatch blocks neighbor formation entirely — it only stalls ExStart/Exchange, neighbor still reaches 2-Way first.

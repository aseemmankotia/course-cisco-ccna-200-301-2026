## Chapter 1: Network Components, Topologies, and Cabling — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | 802.3af vs 802.3at (PoE) power delivered at the source port? | 802.3af: 15.4W. 802.3at (PoE+): 30W. Exam tip: subtract cable loss to get device-received power — 12.95W (af) and 25.5W (at). |
| 2 | 802.3bt Type 3 and Type 4 (UPOE/PoE++) max power at source? | Type 3: 60W. Type 4: 100W. Used for devices like PTZ cameras, video phones, and some access points needing high power. |
| 3 | Cat6 UTP max distance/speed vs Cat6a? | Cat6: 1Gbps up to 100m, or 10Gbps up to only 55m. Cat6a: 10Gbps up to full 100m. Exam tip: Cat6a is the minimum standard reliably supporting 10GBASE-T at 100m. |
| 4 | Multimode fiber vs Single-mode fiber — key differences? | Multimode: LED/laser, shorter distances (~300-550m at 10G), orange/aqua jacket, cheaper optics, larger core. Single-mode: laser only, long distances (10s of km), yellow jacket, more expensive optics, smaller core. |
| 5 | Router vs Layer 3 switch — when to choose which? | Router: WAN connectivity (serial, DSL, cellular), NAT, complex routing protocol support. L3 switch: fast hardware-based inter-VLAN routing via SVIs within a LAN/campus, no native WAN interfaces. |
| 6 | 2-tier vs 3-tier vs spine-leaf topology — use case for each? | 3-tier: core/distribution/access, large campus networks. 2-tier: collapsed core+distribution, small/medium campus. Spine-leaf: data centers with heavy east-west traffic, every leaf connects to every spine. |
| 7 | What is the role of a WLC (Wireless LAN Controller)? | Centrally manages lightweight APs via CAPWAP tunnels — handles config push, RF management, roaming, and security policy across many APs. |
| 8 | IOS command to check PoE power usage on a switch? | show power inline — displays per-port PoE allocation, admin/oper state, and device class. Exam tip: use this to troubleshoot devices not powering up. |
| 9 | IOS command to check interface errors (CRC, collisions, input/output errors)? | show interfaces [interface-id] — look for CRC errors (bad cabling/duplex mismatch) and collisions (half-duplex issues). Exam tip: high CRC = cabling problem; late collisions = duplex mismatch. |
| 10 | On-prem vs cloud architecture — core conceptual difference? | On-prem: organization owns and manages all infrastructure (CapEx). Cloud: third-party provider owns/manages infrastructure, consumed as a service (OpEx), typically elastic and scalable on demand. |
| 11 | Firewall vs router ACL — key functional difference? | Router ACL: stateless, filters based on static rules (source/dest IP, port) per packet. Firewall: stateful, tracks connection state and automatically permits legitimate return traffic. |
| 12 | Common exam trap: PoE budget calculation | Total switch PoE budget ÷ per-device power draw = max devices. Always round DOWN (partial devices can't be powered). Don't confuse per-port max with total switch budget. |

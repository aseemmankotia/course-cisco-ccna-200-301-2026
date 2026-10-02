## Chapter 3: VLANs, 802.1Q Trunking, and L2 Discovery Protocols — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | CDP default advertisement interval and holdtime? | Advertised every 60 seconds; holdtime 180 seconds. Exam tip: if a CDP neighbor entry ages out, no update was received within the holdtime window. |
| 2 | LLDP default transmit interval and hold time? | Transmit every 30 seconds; hold time 120 seconds (TTL = 4x transmit interval). Exam tip: LLDP timers differ from CDP's 60s/180s — don't mix them up. |
| 3 | What is the default native VLAN on a Cisco trunk port? | VLAN 1. Exam tip: best practice is to change it to an unused VLAN to reduce native VLAN mismatch and security risk. |
| 4 | Normal-range vs extended-range VLAN IDs? | Normal range: 1–1005 (stored in vlan.dat, VTP-advertised). Extended range: 1006–4094 (requires VTP transparent mode on older switches to configure locally). Exam tip: extended VLANs aren't propagated by VTP versions 1/2. |
| 5 | CDP vs LLDP — key difference? | CDP = Cisco-proprietary, Cisco devices only. LLDP = IEEE 802.1AB, vendor-neutral, works across multi-vendor gear. Exam tip: use LLDP when non-Cisco devices need discovery. |
| 6 | Command to assign a switchport to VLAN 20 as an access port? | interface gi0/1 → switchport mode access → switchport access vlan 20. Exam tip: 'switchport access vlan' is ignored if the port is in trunk mode. |
| 7 | Commands to configure a port as an 802.1Q trunk? | switchport trunk encapsulation dot1q (if switch supports ISL) → switchport mode trunk. Exam tip: newer switches with only dot1q support skip the encapsulation command. |
| 8 | Command to set the native VLAN on a trunk port? | switchport trunk native vlan <id>. Exam tip: both ends of the trunk MUST match or you get a native VLAN mismatch warning via CDP. |
| 9 | Command to restrict which VLANs are allowed across a trunk? | switchport trunk allowed vlan <list>. Exam tip: use 'add', 'remove', or 'except' keywords to modify the list instead of overwriting it entirely. |
| 10 | Command to view full CDP neighbor info including IP address and platform? | show cdp neighbors detail (or 'show cdp entry *'). Exam tip: 'show cdp neighbors' (without detail) omits IP address and software version. |
| 11 | Command to verify VLAN-to-port assignments on access ports? | show vlan brief. Exam tip: trunk ports do NOT appear under any VLAN in this output — use 'show interfaces trunk' to verify trunks instead. |
| 12 | Effect of a native VLAN mismatch between two trunked switches? | Untagged traffic sent as native VLAN on one side is received into the different native VLAN on the other side, causing VLAN traffic leakage and a CDP-logged warning. Exam tip: this does NOT bring the trunk down — traffic still flows for tagged VLANs. |

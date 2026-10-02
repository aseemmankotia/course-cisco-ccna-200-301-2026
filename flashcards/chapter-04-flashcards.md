## Chapter 4: EtherChannel, Rapid PVST+, and WLAN/WLC Basics — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | LACP mode combinations that successfully form an EtherChannel | active-active, active-passive. Passive-passive FAILS (no side initiates). Exam tip: at least one side must be active. |
| 2 | PAgP mode combinations that successfully form an EtherChannel | desirable-desirable, desirable-auto. Auto-auto FAILS. PAgP is Cisco proprietary; LACP is IEEE 802.3ad/802.1AX (open standard). |
| 3 | Max active links in a single Cisco EtherChannel bundle (LACP) | 8 active links. LACP can support up to 16 total physical links per bundle (8 active + 8 hot-standby). |
| 4 | Default STP/RSTP bridge priority value and increment | Default priority = 32768. Increments in steps of 4096. Lower priority = more likely to become root. |
| 5 | Components of a Bridge ID (used for root election) | Bridge Priority (0–65535, default 32768) + Extended System ID (VLAN ID) + MAC address. Lowest overall Bridge ID wins root. |
| 6 | RSTP port states (3 total) | Discarding, Learning, Forwarding. Legacy STP has 5: Blocking, Listening, Learning, Forwarding, Disabled. RSTP merges Blocking+Listening into Discarding. |
| 7 | RSTP port roles (4 total) | Root (best path to root, forwarding), Designated (forwards onto a segment), Alternate (backup to root port, discarding), Backup (backup to designated port on shared segment, discarding). |
| 8 | PortFast purpose and where to use it | Skips Listening/Learning states, port goes straight to Forwarding. Use ONLY on access ports connected to end devices, never on switch-to-switch links. |
| 9 | BPDU Guard behavior when a BPDU arrives on a PortFast port | Immediately err-disables the port. Command: 'spanning-tree bpduguard enable' (interface) or 'spanning-tree portfast bpduguard default' (global, applies to all PortFast ports). |
| 10 | Command to set EtherChannel load-balancing to source/destination IP | port-channel load-balance src-dst-ip (global config command). Other options: src-mac, dst-mac, src-dst-mac, src-ip, dst-ip, src-dst-port. |
| 11 | WPA2 vs WPA3 key exchange method | WPA2 uses PSK with 4-way handshake (vulnerable to offline dictionary attacks). WPA3 uses SAE (Simultaneous Authentication of Equals), providing forward secrecy and resistance to offline attacks. |
| 12 | Cisco WLC QoS profiles, highest to lowest priority | Platinum (voice) > Gold (video) > Silver (best effort, default) > Bronze (background/scavenger). |

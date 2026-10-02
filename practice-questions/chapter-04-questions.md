## Chapter 4: EtherChannel, Rapid PVST+, and WLAN/WLC Basics — Practice Questions

**Q1.** Two switches, SW1 and SW2, are connected by two links intended to form an EtherChannel. SW1 is configured with 'channel-group 1 mode passive' on both interfaces. SW2 is also configured with 'channel-group 1 mode passive' on both interfaces. What is the result?

A) The EtherChannel forms normally using LACP
B) The EtherChannel does not form because both sides are passive
C) The EtherChannel forms but only one link is active
D) The EtherChannel forms using PAgP as a fallback

<details>
<summary>Answer</summary>

**Correct: B**

LACP requires at least one side to actively initiate negotiation. Passive-passive means neither side sends LACP packets first, so no channel forms.

**Why the others are wrong:**
- LACP needs an active initiator; passive-passive never negotiates
- No negotiation occurs at all, so no link comes up, not just one
- PAgP and LACP are separate protocols and never interoperate as a fallback

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** Three switches run Rapid PVST+ for VLAN 10. SW1 has priority 24576 and MAC 0011.1111.1111. SW2 has priority 32768 and MAC 0022.2222.2222. SW3 has priority 24576 and MAC 0000.3333.3333. Which switch becomes the root bridge for VLAN 10?

A) SW1, because it was configured first
B) SW2, because default priority always wins ties
C) SW1, because its MAC address is numerically lower than SW3's when read left to right
D) SW3, because it has the lowest priority tied with SW1 but a lower MAC address

<details>
<summary>Answer</summary>

**Correct: D**

Root bridge election compares Bridge ID (priority + extended system ID + MAC). SW1 and SW3 tie on priority (24576, lower than SW2's 32768), so the tiebreaker is lowest MAC address; 0000.3333.3333 is lower than 0011.1111.1111.

**Why the others are wrong:**
- Configuration order has no bearing on root election, only Bridge ID
- Default priority (32768) is the highest of the three, so SW2 cannot win
- 0011.1111.1111 is numerically higher than 0000.3333.3333, so SW1 loses the tiebreaker

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A company wants guest Wi-Fi users to connect without sharing a pre-shared key, while still protecting against offline dictionary attacks even if traffic is captured. Which WLAN security setting on the WLC BEST meets this requirement?

A) WPA3-Personal (SAE)
B) WPA2-Personal with a long passphrase
C) Open authentication with a captive portal
D) WPA2-Enterprise with 802.1X

<details>
<summary>Answer</summary>

**Correct: A**

WPA3-Personal uses SAE (Simultaneous Authentication of Equals), which provides forward secrecy and resists offline dictionary attacks even against captured handshake traffic, without requiring per-user credentials.

**Why the others are wrong:**
- WPA2-Personal still uses a 4-way handshake vulnerable to offline dictionary attacks if the passphrase is weak
- Open authentication provides no encryption of the wireless link itself
- WPA2-Enterprise requires per-user credentials and an authentication server, which contradicts the 'no shared key' guest scenario intent of simple SAE-based security

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** In RSTP, a non-root switch has two paths toward the root bridge. One path has the lowest cost and is placed in the forwarding state. What is this port's role?

A) Root port
B) Designated port
C) Alternate port
D) Backup port

<details>
<summary>Answer</summary>

**Correct: A**

The root port is the single port on a non-root switch with the best (lowest cost) path to the root bridge, and it is placed in the forwarding state.

**Why the others are wrong:**
- Designated ports forward traffic onto a segment but are not the switch's best path to the root
- Alternate ports remain in the discarding state as a backup path to the root
- Backup ports are a rare role on shared segments providing a backup to a designated port, not the path to root

</details>

---

**Q5.** A network administrator is configuring QoS profiles on a WLC and needs to ensure voice traffic receives the highest priority over video and data. Which QoS profile should be applied to the voice WLAN?

A) Gold
B) Silver
C) Bronze
D) Platinum

<details>
<summary>Answer</summary>

**Correct: D**

Platinum is the highest QoS profile on Cisco WLCs and is intended for voice traffic requiring the lowest latency and highest priority.

**Why the others are wrong:**
- Gold is intended for video traffic, one tier below Platinum
- Silver is the default best-effort profile, used for standard data
- Bronze is the lowest profile, intended for background/scavenger traffic

</details>

---

**Q6.** Which command enables BPDU Guard on a single access port already configured with PortFast?

A) spanning-tree guard root
B) spanning-tree bpduguard enable
C) spanning-tree portfast bpduguard default
D) spanning-tree bpdufilter enable

<details>
<summary>Answer</summary>

**Correct: B**

'spanning-tree bpduguard enable' is the interface-level command that enables BPDU Guard on that specific port, err-disabling it if a BPDU is received.

**Why the others are wrong:**
- 'spanning-tree guard root' enables Root Guard, a different feature that prevents a port from becoming root port
- This is the global configuration command that enables BPDU Guard on ALL PortFast-enabled ports, not a single port
- BPDU filter suppresses BPDUs rather than err-disabling the port, a different mechanism entirely

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** An engineer wants EtherChannel traffic to be load-balanced based on both the source and destination IP address to improve distribution across links carrying routed traffic. Which global configuration command accomplishes this?

A) port-channel load-balance src-dst-mac
B) port-channel load-balance src-dst-ip
C) port-channel load-balance src-ip
D) channel-group load-balance src-dst-ip

<details>
<summary>Answer</summary>

**Correct: B**

'port-channel load-balance src-dst-ip' is the correct global configuration command that hashes based on both source and destination IP addresses.

**Why the others are wrong:**
- src-dst-mac balances on MAC addresses, not IP addresses, which is less effective for routed traffic
- src-ip only considers the source IP, ignoring the destination, giving less balanced distribution
- 'channel-group' is not the correct keyword for this global command; it is used at the interface level to assign ports to a channel

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** How many port states does RSTP (802.1w) use, compared to legacy STP (802.1D)?

A) RSTP uses 3 states; STP uses 5 states
B) RSTP uses 5 states; STP uses 3 states
C) Both use the same 5 states
D) RSTP uses 2 states; STP uses 4 states

<details>
<summary>Answer</summary>

**Correct: A**

RSTP consolidates Blocking and Listening into a single Discarding state, resulting in 3 states (Discarding, Learning, Forwarding), while legacy STP uses 5 (Blocking, Listening, Learning, Forwarding, Disabled).

**Why the others are wrong:**
- This reverses the actual state counts of RSTP and STP
- N/A — this is the correct answer
- Neither protocol uses only 2 or 4 states; the counts are 3 and 5 respectively

</details>

---


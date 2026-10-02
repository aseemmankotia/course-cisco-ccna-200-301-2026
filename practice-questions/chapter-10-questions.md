## Chapter 10: ACLs, Layer 2 Security, and Wireless Security — Practice Questions

**Q1.** A company wants to deny host 10.10.10.5 from reaching server 172.16.1.100 on TCP port 443, while allowing 10.10.10.5 to reach all other destinations without restriction. Which solution and placement is BEST?

A) Standard ACL denying 10.10.10.5 placed on the interface closest to 172.16.1.100
B) Standard ACL denying 10.10.10.5 placed on the interface closest to 10.10.10.5
C) Extended ACL denying 10.10.10.5 to 172.16.1.100 on port 443, placed on the interface closest to 172.16.1.100
D) Extended ACL denying 10.10.10.5 to 172.16.1.100 on port 443, placed on the interface closest to 10.10.10.5

<details>
<summary>Answer</summary>

**Correct: D**

Extended ACLs can match source AND destination AND port, satisfying the requirement to allow the host access everywhere else. Extended ACLs should be placed as close to the source as possible to avoid wasting bandwidth carrying traffic across the network before it's dropped.

**Why the others are wrong:**
- Standard ACLs can only filter by source address — they cannot restrict traffic to a single destination/port while allowing everything else.
- Same standard ACL limitation applies regardless of placement — it would block ALL traffic from 10.10.10.5, not just the traffic to the specific server/port.
- Extended ACL logic is correct but placement near the destination wastes bandwidth — the denied traffic would traverse the entire network before being dropped.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A network engineer needs to block all traffic sourced from subnet 192.168.10.0/24 from reaching the entire 192.168.20.0/24 network, and no other traffic needs filtering. Where should this standard ACL be applied?

A) On the interface closest to the source subnet (192.168.10.0/24)
B) On every interface in the transit path
C) On the interface closest to the destination subnet (192.168.20.0/24)
D) On the router with the lowest OSPF router ID

<details>
<summary>Answer</summary>

**Correct: C**

Standard ACLs only see the source address, so placing them near the source risks accidentally blocking traffic intended for other legitimate destinations. Best practice is to place standard ACLs close to the destination they're meant to protect.

**Why the others are wrong:**
- Placing a standard ACL near the source would block traffic to ALL destinations from that subnet, not just 192.168.20.0/24 — this is the classic exam trap.
- Applying to every interface is unnecessary overhead and not how ACL placement rules work.
- Router ID has nothing to do with ACL placement decisions.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A switch port configured with port security using the 'shutdown' violation mode receives a frame from an unauthorized MAC address. What happens?

A) The frame is silently dropped and no counter is incremented
B) The port transitions to err-disabled state and stops forwarding all traffic until manually re-enabled
C) The frame is dropped, a syslog message is generated, and the violation counter increments, but the port stays up
D) The switch automatically relearns the new MAC address and replaces the old one

<details>
<summary>Answer</summary>

**Correct: B**

Shutdown is the default and most severe violation mode — the port is put into err-disabled state, requiring 'shutdown' then 'no shutdown' (or errdisable recovery) to restore it.

**Why the others are wrong:**
- This describes 'protect' mode, which drops silently with no logging or counter increment.
- This describes 'restrict' mode, which logs and counts violations but keeps the port forwarding traffic from allowed MACs.
- Port security never auto-replaces a learned MAC on violation — that's not how any of the three modes behave.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Users on a VLAN suddenly receive incorrect IP addressing and a default gateway pointing to an attacker's laptop instead of the legitimate router. Which feature should have been configured to prevent this?

A) Dynamic ARP Inspection (DAI)
B) Port security with sticky MAC
C) 802.1X authentication
D) DHCP snooping

<details>
<summary>Answer</summary>

**Correct: D**

DHCP snooping blocks DHCP server responses (offers/acks) on untrusted ports, preventing a rogue DHCP server from handing out malicious IP configuration and gateway information.

**Why the others are wrong:**
- DAI validates ARP packets against the DHCP snooping binding table to stop ARP spoofing — it doesn't stop a rogue DHCP server from issuing leases in the first place.
- Port security limits which MAC addresses can send frames on a port; it doesn't inspect or block DHCP server messages.
- 802.1X authenticates devices/users onto the network but does nothing to filter rogue DHCP traffic.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A company needs per-user authentication with centralized credential management (RADIUS) for wireless clients connecting to the corporate SSID, rather than a single shared password. Which configuration meets this requirement?

A) WPA2-Enterprise or WPA3-Enterprise with 802.1X
B) WPA2-Personal with a long, complex PSK
C) WPA3-Personal using SAE
D) Open authentication with a captive portal

<details>
<summary>Answer</summary>

**Correct: A**

802.1X (Enterprise mode) provides per-user authentication against a RADIUS server, giving individual credentials and centralized control — exactly what's required here.

**Why the others are wrong:**
- PSK, even a strong one, is a single shared secret for everyone — it does not provide per-user identity or centralized RADIUS auth.
- WPA3-Personal/SAE improves the PSK exchange (resists offline dictionary attacks) but is still a single shared passphrase, not per-user.
- Open authentication with a captive portal provides no encryption and typically only a web-based login, not RADIUS-integrated per-user 802.1X auth.

</details>

---

**Q6.** Which wildcard mask correctly matches all hosts in the 172.16.32.0/22 network in an ACL statement?

A) 0.0.0.255
B) 0.0.3.255
C) 0.0.1.255
D) 255.255.252.0

<details>
<summary>Answer</summary>

**Correct: B**

/22 = subnet mask 255.255.252.0. Wildcard = 255.255.255.255 minus subnet mask = 0.0.3.255, which matches the block of 1024 addresses (172.16.32.0–172.16.35.255).

**Why the others are wrong:**
- 0.0.0.255 is the wildcard for a /24, not /22 — matches only 256 addresses.
- 0.0.1.255 corresponds to a /23 network (512 addresses), one bit block too small.
- 255.255.252.0 is the actual subnet mask, not the inverted wildcard mask — a common mix-up on the exam.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which command correctly configures a switch port to allow a maximum of 2 learned MAC addresses and place the port in err-disabled state on a violation?

A) switchport port-security maximum 2 ; switchport port-security violation protect
B) switchport port-security maximum 2 ; switchport port-security violation shutdown
C) switchport port-security maximum 2 ; switchport port-security violation restrict
D) switchport port-security mac-address maximum 2 ; switchport port-security mode shutdown

<details>
<summary>Answer</summary>

**Correct: B**

'switchport port-security maximum 2' sets the limit, and 'switchport port-security violation shutdown' (the default mode) err-disables the port on a violation.

**Why the others are wrong:**
- Protect mode drops violating traffic silently and does NOT err-disable the port.
- Restrict mode logs and counts violations but does NOT err-disable the port.
- This uses invalid Cisco IOS syntax — the keywords 'mac-address maximum' and 'mode shutdown' don't exist for port security configuration.

</details>

---

**Q8.** What is the primary functional difference between a standard ACL and an extended ACL in Cisco IOS?

A) Standard ACLs filter based on source address only; extended ACLs filter based on source, destination, protocol, and port
B) Standard ACLs can only be applied outbound; extended ACLs can only be applied inbound
C) Standard ACLs are always named; extended ACLs are always numbered
D) Standard ACLs support both permit and deny; extended ACLs support only deny

<details>
<summary>Answer</summary>

**Correct: A**

This is the fundamental distinction: standard ACLs (1-99, 1300-1999) match source IP only, while extended ACLs (100-199, 2000-2699) can match source, destination, protocol, and Layer 4 ports for granular filtering.

**Why the others are wrong:**
- Both standard and extended ACLs can be applied in either direction (inbound or outbound) on an interface — direction is not what distinguishes them.
- Both ACL types support numbered or named formats — naming convention is independent of the filtering capability.
- Both ACL types support permit and deny statements equally.

</details>

---


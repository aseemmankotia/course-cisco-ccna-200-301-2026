## Chapter 3: VLANs, 802.1Q Trunking, and L2 Discovery Protocols — Practice Questions

**Q1.** Two switches, SW1 and SW2, are connected via a trunk link. SW1's trunk port is configured with 'switchport trunk native vlan 10' and SW2's trunk port still uses the default native VLAN. Console logs show a CDP native VLAN mismatch error. What is the MOST likely operational impact?

A) Untagged traffic from VLAN 10 on SW1 will be received into VLAN 1 on SW2, causing traffic to leak between VLANs
B) The trunk link will not pass any traffic until the mismatch is fixed
C) Both switches will automatically renegotiate to a common native VLAN using DTP
D) The port will be placed into err-disabled state immediately

<details>
<summary>Answer</summary>

**Correct: A**

Native VLAN traffic is sent untagged across a trunk. If the two ends define different native VLANs, the untagged frames land in whatever VLAN the receiving switch has configured as native, causing traffic to cross VLAN boundaries unexpectedly.

**Why the others are wrong:**
- The link stays up and forwards tagged VLAN traffic normally; only the untagged native VLAN traffic is affected
- DTP negotiates trunk mode/encapsulation, not native VLAN — native VLAN mismatch is only detected via CDP, not auto-corrected
- Err-disable is triggered by things like BPDU guard or port security violations, not native VLAN mismatch (which only generates a syslog/CDP warning)

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A network engineer runs 'show cdp neighbors detail' on SW1 but the connected Aruba access point does not appear, even though the physical link is up and passing traffic. What is the MOST likely explanation?

A) CDP is disabled globally on SW1
B) The trunk native VLAN is mismatched between SW1 and the AP
C) CDP only discovers Cisco switches, never endpoints like access points
D) The Aruba AP does not support CDP and instead uses LLDP, which requires 'show lldp neighbors detail' on SW1

<details>
<summary>Answer</summary>

**Correct: D**

CDP is Cisco-proprietary and most non-Cisco devices, including many Aruba/HPE access points, only support LLDP (IEEE 802.1AB). To see the neighbor, the engineer must check LLDP on SW1.

**Why the others are wrong:**
- If CDP were globally disabled, no neighbors at all would appear on any interface — the scenario implies other Cisco neighbors likely still show
- A native VLAN mismatch only affects untagged trunk traffic and generates a warning; it does not remove a device from CDP/LLDP neighbor tables
- CDP can discover any Cisco device including Cisco APs, and can also see directly connected non-Cisco devices if they support CDP — but here the AP doesn't

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A company is deploying a mixed vendor environment with Cisco switches, Juniper routers, and third-party IP phones from a non-Cisco vendor. They need a single Layer 2 discovery protocol that all devices support for topology mapping. Which protocol should they standardize on?

A) CDP, because it provides more detailed information than any alternative
B) LLDP, because it is an IEEE vendor-neutral standard supported across multi-vendor equipment
C) DTP, because it dynamically discovers neighboring switches
D) VTP, because it synchronizes VLAN information across all switches in the domain

<details>
<summary>Answer</summary>

**Correct: B**

LLDP (IEEE 802.1AB) is the vendor-neutral discovery protocol designed to work across multi-vendor equipment, exactly the requirement in a mixed Cisco/Juniper/third-party environment.

**Why the others are wrong:**
- CDP is Cisco-proprietary and will not be recognized by Juniper or most third-party devices
- DTP (Dynamic Trunking Protocol) negotiates trunk links between two Cisco switches — it is not a discovery/topology protocol and is Cisco-proprietary
- VTP synchronizes VLAN databases across Cisco switches in the same domain — unrelated to device discovery and also Cisco-proprietary

</details>

---

**Q4.** Which command correctly restricts a trunk port to carry only VLANs 10, 20, and 30, removing all others from the allowed list?

A) switchport trunk native vlan 10,20,30
B) switchport trunk allowed vlan 10,20,30
C) switchport access vlan 10,20,30
D) switchport trunk encapsulation dot1q 10,20,30

<details>
<summary>Answer</summary>

**Correct: B**

'switchport trunk allowed vlan <list>' explicitly sets the VLANs permitted across a trunk, overwriting the default allow-all list.

**Why the others are wrong:**
- 'switchport trunk native vlan' sets a single VLAN as the untagged native VLAN, not a list of allowed VLANs, and does not accept a comma list this way
- 'switchport access vlan' configures an access port's VLAN assignment and is invalid syntax/context for a trunk port carrying multiple VLANs
- 'switchport trunk encapsulation dot1q' only selects the tagging protocol (dot1q vs ISL) and takes no VLAN list argument

</details>

---

**Q5.** An engineer runs 'show vlan brief' on a switch and notices that GigabitEthernet0/1, which is physically connected and passing traffic to another switch, does not appear listed under any VLAN. What is the MOST likely reason?

A) The port is configured as a trunk, and trunk ports are not listed under any single VLAN in 'show vlan brief' output
B) The port is shut down administratively
C) The port has no IP address configured
D) The switch has not learned any MAC addresses on that port yet

<details>
<summary>Answer</summary>

**Correct: A**

'show vlan brief' only lists access (untagged) port-to-VLAN mappings. Trunk ports, which carry multiple tagged VLANs, are intentionally excluded from this per-VLAN port listing.

**Why the others are wrong:**
- An administratively shut down port would still show under its assigned VLAN (if access) with a down status — it wouldn't disappear from the table entirely if access mode
- Switch ports operate at Layer 2 and do not require an IP address to appear in VLAN tables
- MAC address learning is unrelated to whether a port appears in 'show vlan brief' output

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** Which single command sequence correctly assigns interface FastEthernet0/5 as an access port in VLAN 30?

A) interface fa0/5 ; switchport mode trunk ; switchport access vlan 30
B) interface fa0/5 ; switchport mode access ; switchport access vlan 30
C) interface fa0/5 ; vlan 30 ; switchport access vlan 30
D) interface fa0/5 ; switchport trunk allowed vlan 30

<details>
<summary>Answer</summary>

**Correct: B**

Setting 'switchport mode access' followed by 'switchport access vlan 30' correctly and unambiguously configures the port as a static access port in VLAN 30.

**Why the others are wrong:**
- Setting 'switchport mode trunk' contradicts assigning a single access VLAN — 'switchport access vlan' is ignored while the port is in trunk mode
- 'vlan 30' as an interface-level subcommand is invalid syntax; VLAN creation happens in global 'vlan database' or 'vlan 30' global config mode, not under the interface
- 'switchport trunk allowed vlan' only applies to trunk ports and would not put the port into access mode for VLAN 30

</details>

---

**Q7.** A branch office switch needs to send its VLAN and topology information only to directly connected Cisco IP phones for auto-QoS/voice VLAN discovery, while minimizing information leaked to non-Cisco devices. Which protocol is the BEST fit for this specific requirement?

A) CDP, because Cisco IP phones use CDP by default to learn the voice VLAN from the switch
B) LLDP, because it is the modern industry standard
C) VTP, because it propagates VLAN configuration automatically
D) STP, because it prevents loops on the access port

<details>
<summary>Answer</summary>

**Correct: A**

Cisco IP phones rely on CDP by default to receive voice VLAN assignment and power negotiation information from the connected Cisco switch — this is a classic, heavily tested exam scenario.

**Why the others are wrong:**
- LLDP is used for multi-vendor phones (LLDP-MED) but the scenario specifically involves Cisco phones, where CDP is the default and simplest mechanism
- VTP synchronizes VLAN databases between switches, not between a switch and an endpoint phone
- STP prevents Layer 2 loops but has no role in VLAN/voice VLAN discovery

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the fundamental difference between CDP and LLDP as data link layer discovery protocols?

A) CDP operates at Layer 3 while LLDP operates at Layer 2
B) CDP can only discover routers while LLDP can only discover switches
C) CDP is Cisco-proprietary while LLDP is an IEEE (802.1AB) vendor-neutral standard
D) CDP requires IP addressing to function while LLDP does not

<details>
<summary>Answer</summary>

**Correct: C**

The core distinction tested on the exam is that CDP is proprietary to Cisco devices, while LLDP (defined by IEEE 802.1AB) is an open, vendor-neutral standard usable across mixed-vendor networks.

**Why the others are wrong:**
- Both CDP and LLDP operate at Layer 2, advertised in Ethernet frames directly to directly connected neighbors
- Both protocols can discover any directly connected neighbor device type (switches, routers, phones, APs) that supports them — neither is restricted to one device category
- Neither protocol requires Layer 3 IP addressing to operate; they function purely at Layer 2 using multicast MAC addresses

</details>

---


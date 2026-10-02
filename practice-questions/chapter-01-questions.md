## Chapter 1: Network Components, Topologies, and Cabling — Practice Questions

**Q1.** A company is connecting two buildings that are 8 km apart and needs a link immune to electromagnetic interference. Which cabling type should be used?

A) Cat6a UTP
B) Multimode fiber (OM3)
C) Coaxial cable
D) Single-mode fiber

<details>
<summary>Answer</summary>

**Correct: D**

Single-mode fiber supports distances up to 40+ km depending on transceiver and is immune to EMI, making it the only viable option for an 8 km run.

**Why the others are wrong:**
- Cat6a UTP is limited to 100m and is susceptible to EMI over long copper runs.
- Multimode fiber (OM3) is typically limited to 300-550m at 10Gbps due to modal dispersion, far short of 8km.
- Coaxial cable is legacy technology, not used for modern building-to-building links and has severe distance/EMI limitations.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A data center architect needs a topology that provides predictable, low latency for high-volume east-west traffic between servers, with every leaf switch connected to every spine switch. Which topology fits this requirement?

A) 3-tier hierarchical
B) 2-tier collapsed core
C) Hub-and-spoke WAN
D) Spine-leaf

<details>
<summary>Answer</summary>

**Correct: D**

Spine-leaf topology connects every leaf to every spine, ensuring any server-to-server path traverses exactly one spine hop, giving consistent low latency for east-west traffic.

**Why the others are wrong:**
- 3-tier hierarchical (core/distribution/access) is optimized for north-south client-to-server traffic, not high east-west volume.
- 2-tier collapsed core removes the distribution layer but still follows a hierarchical north-south design, not optimized for east-west.
- Hub-and-spoke is a WAN topology model for connecting remote sites to a central hub, irrelevant to intra-data-center server traffic.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A branch office needs inter-VLAN routing between its internal VLANs only, with no requirement for WAN connectivity, NAT, or dynamic routing to an ISP. Which device meets the requirement most cost-effectively?

A) Layer 3 switch
B) ISR router
C) Layer 2 switch with trunking
D) Next-generation firewall

<details>
<summary>Answer</summary>

**Correct: A**

A Layer 3 switch performs hardware-accelerated inter-VLAN routing using SVIs and is cheaper per port than a router when no WAN interfaces are needed.

**Why the others are wrong:**
- An ISR router is designed for WAN connectivity (serial, DSL, cellular) and NAT, which is unnecessary and more expensive here.
- A Layer 2 switch cannot route between VLANs; it only switches within a broadcast domain.
- A next-generation firewall is a security device, not optimized or intended for inter-VLAN routing at scale.

</details>

---

**Q4.** An enterprise plans to deploy 200 lightweight access points across a campus and requires centralized configuration, RF management, and roaming support. Which device is required?

A) Standalone autonomous AP
B) Layer 3 switch
C) Wireless LAN Controller (WLC)
D) Router with wireless module

<details>
<summary>Answer</summary>

**Correct: C**

A WLC centrally manages lightweight APs via CAPWAP, handling configuration push, RF optimization, and seamless roaming across the campus.

**Why the others are wrong:**
- Standalone autonomous APs are managed individually and don't scale for centralized management of 200 units.
- A Layer 3 switch handles routing/switching but has no role in wireless AP management or CAPWAP termination.
- A router with a wireless module provides local wireless for small deployments, not centralized enterprise-scale control.

</details>

---

**Q5.** A network engineer needs to enforce stateful inspection of traffic between the internal LAN and the internet, tracking connection state for return traffic. Which device should be deployed at the edge?

A) Firewall
B) Router with standard ACL
C) Layer 2 switch
D) Wireless LAN Controller

<details>
<summary>Answer</summary>

**Correct: A**

A firewall performs stateful inspection, tracking the state of active connections and automatically permitting return traffic, unlike stateless ACLs.

**Why the others are wrong:**
- A router with a standard ACL is stateless and filters based only on source IP, not connection state.
- A Layer 2 switch operates at the data link layer and has no capability to inspect or filter based on connection state.
- A WLC manages wireless APs and has no role in stateful traffic inspection at the network edge.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A PTZ security camera requires 30W to operate and is connected to a switch port that only supports the 802.3af standard. What is the result?

A) The camera powers on normally since 802.3af supports up to 30W
B) The camera powers on at reduced performance using negotiated wattage
C) The camera fails to power on because 802.3af provides a maximum of 15.4W at the source
D) The switch automatically upgrades the port to 802.3at to meet demand

<details>
<summary>Answer</summary>

**Correct: C**

802.3af (PoE) delivers a maximum of 15.4W at the switch port (12.95W at the device after cable loss), insufficient for a 30W camera; 802.3at (PoE+) is required.

**Why the others are wrong:**
- 802.3af caps at 15.4W, not 30W — this confuses it with the PoE+ standard.
- PoE standards don't operate on a sliding negotiated scale that allows partial power delivery beyond the standard's max.
- Switch ports cannot auto-upgrade hardware standards; 802.3at requires supporting hardware, not a software toggle alone.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A switch has a total PoE power budget of 370W and only supports 802.3at (PoE+), delivering 25.5W per device at the powered device. What is the maximum number of PoE+ devices the switch can fully power?

A) 12
B) 16
C) 14
D) 20

<details>
<summary>Answer</summary>

**Correct: C**

370W ÷ 25.5W per device = 14.5, and since partial devices cannot be powered, the switch can fully support 14 PoE+ devices.

**Why the others are wrong:**
- 12 undercounts the available budget by too large a margin.
- 16 devices would require 408W, exceeding the 370W budget.
- 20 devices would require 510W, far exceeding the 370W budget.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly differentiates on-premises architecture from cloud architecture at a conceptual level?

A) On-premises places infrastructure ownership and management with the organization, while cloud shifts infrastructure management to a third-party provider
B) On-premises requires no capital expenditure while cloud requires large upfront hardware purchases
C) Cloud architecture cannot scale elastically, while on-premises can scale instantly
D) On-premises and cloud architectures are functionally identical in terms of management responsibility

<details>
<summary>Answer</summary>

**Correct: A**

On-premises infrastructure is owned, hosted, and managed by the organization itself, while cloud architecture delegates infrastructure ownership and management to a third-party provider, typically via a service model (IaaS/PaaS/SaaS).

**Why the others are wrong:**
- This reverses reality — on-premises typically requires large capital expenditure for hardware, while cloud shifts to operational expenditure.
- This reverses the actual scaling characteristics — cloud is known for elastic scalability, while on-premises scaling requires physical hardware procurement.
- The two models differ fundamentally in who owns and manages the infrastructure, so they are not functionally identical.

</details>

---


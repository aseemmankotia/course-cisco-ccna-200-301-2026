## Chapter 11: Controller-Based Networking, REST APIs, and JSON — Practice Questions

**Q1.** A network architect wants to separate the control plane from the data plane, allowing a central system to push configuration and policy to hundreds of switches simultaneously instead of configuring each device's CLI individually. Which architecture BEST meets this requirement?

A) Traditional per-device CLI management
B) A stacked switch topology
C) Controller-based (SDN) architecture
D) Manual VLAN trunking on each switch

<details>
<summary>Answer</summary>

**Correct: C**

Controller-based/SDN architecture centralizes the control plane in a controller (e.g., Cisco DNA Center), which pushes configuration and policy to the underlying (data plane) devices, eliminating box-by-box CLI management.

**Why the others are wrong:**
- Traditional CLI management is exactly the box-by-box approach the architect wants to avoid.
- Stacking only groups physical switches into one logical unit for management on-box; it doesn't provide centralized policy across the whole network.
- Manual VLAN trunking is a Layer 2 config task, unrelated to centralized control/data plane separation.

</details>

---

**Q2.** An engineer sends an HTTP request to a Cisco DNA Center REST API endpoint solely to retrieve the current list of managed devices without changing anything. Which HTTP verb should be used?

A) POST
B) GET
C) PUT
D) DELETE

<details>
<summary>Answer</summary>

**Correct: B**

GET maps to the CRUD 'Read' operation and is used to retrieve a resource's current state without modifying it.

**Why the others are wrong:**
- POST maps to 'Create' and is used to add a new resource, not retrieve data.
- PUT maps to 'Update' and replaces/modifies an existing resource.
- DELETE maps to 'Delete' and removes a resource; it does not retrieve data.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** In REST API terminology, which CRUD operation does the HTTP PUT method correspond to?

A) Create
B) Update
C) Read
D) Delete

<details>
<summary>Answer</summary>

**Correct: B**

PUT is used to update/replace an existing resource with the data supplied in the request body.

**Why the others are wrong:**
- Create maps to POST, which adds a new resource.
- Read maps to GET, which retrieves data.
- Delete maps to DELETE, which removes a resource.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A company wants an automation tool that requires no software agent installed on managed devices and pushes configuration changes over SSH from a control node whenever the administrator runs a playbook. Which tool BEST fits this description?

A) Puppet
B) Chef
C) SaltStack (agent mode)
D) Ansible

<details>
<summary>Answer</summary>

**Correct: D**

Ansible is agentless, connects over SSH (or NETCONF/API), and uses a push model where changes are sent out on-demand when a playbook is executed.

**Why the others are wrong:**
- Puppet is agent-based and pull-based — managed nodes periodically pull configuration from the Puppet Master.
- Chef is agent-based and pull-based — a Chef client on each node pulls 'recipes' from a Chef Server.
- SaltStack in agent (minion) mode requires installed software on managed nodes, unlike the agentless requirement stated.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Given the following JSON response from a REST API call:
```
{
  "interfaces": [
    {"name": "Gi0/1", "status": "up"},
    {"name": "Gi0/2", "status": "down"}
  ]
}
```
Which value would you reference to determine the status of the SECOND interface in the array?

A) interfaces[0].status
B) interfaces.status[1]
C) interfaces[1].status
D) interfaces[2].name

<details>
<summary>Answer</summary>

**Correct: C**

JSON arrays are zero-indexed, so the second element in the 'interfaces' array is at index [1], and its 'status' key holds the value 'down'.

**Why the others are wrong:**
- interfaces[0] refers to the FIRST array element (Gi0/1), not the second.
- This syntax is invalid JSON path notation — the index must follow the array name, not the key.
- Index [2] would be out of bounds since only two elements (index 0 and 1) exist in the array, and .name would return the interface name, not status.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A DevOps team wants a human-readable data format that uses indentation instead of brackets/braces and is the native format for Ansible playbooks. Which format should they use?

A) XML
B) JSON
C) YAML
D) CSV

<details>
<summary>Answer</summary>

**Correct: C**

YAML uses indentation (no braces/brackets) and is the standard, most human-readable format for writing Ansible playbooks.

**Why the others are wrong:**
- XML uses opening/closing tags, is verbose, and is not the native Ansible playbook format.
- JSON uses curly braces and brackets for structure; it is machine-friendly but less human-readable than YAML for playbooks.
- CSV is a flat, tabular text format unsuitable for representing nested playbook structures.

</details>

---

**Q7.** In an SDN fabric, which statement correctly describes the relationship between the overlay and the underlay?

A) The underlay is a virtual, logical network built on top of the overlay's physical links
B) The overlay is a virtual network built on top of the underlay, which provides the physical IP connectivity between devices
C) The overlay and underlay refer to the same physical topology viewed at different times
D) The underlay only exists in traditional networks and has no role in an SDN fabric

<details>
<summary>Answer</summary>

**Correct: B**

The underlay is the physical network providing basic IP reachability between fabric devices; the overlay is the virtual/logical network (e.g., VXLAN tunnels) built on top of it to carry tenant traffic and policy.

**Why the others are wrong:**
- This reverses the relationship — the underlay is physical, not virtual, and the overlay sits on top of it, not the other way around.
- They are distinct layers with different purposes (physical transport vs. logical tunneling), not the same topology.
- The underlay is still required in SDN fabrics (like Cisco SD-Access) to physically transport overlay traffic.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which of the following BEST describes a core capability of Cisco DNA Center compared to traditional per-device network management?

A) It provides centralized automation, assurance (analytics/telemetry), and policy-based network management from a single controller
B) It requires administrators to configure each switch's CLI individually for consistency
C) It only supports monitoring and has no configuration push capability
D) It replaces the need for any underlying physical switches or routers

<details>
<summary>Answer</summary>

**Correct: A**

Cisco DNA Center is a centralized controller that provides automation (pushing configs/policy), assurance (network health analytics), and design/policy management, replacing manual box-by-box CLI work.

**Why the others are wrong:**
- This describes the traditional model DNA Center is meant to replace, not DNA Center's own function.
- DNA Center does more than monitor — it actively automates provisioning and configuration via APIs.
- DNA Center manages and controls physical infrastructure; it does not eliminate the need for physical devices.

</details>

---


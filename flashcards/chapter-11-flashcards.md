## Chapter 11: Controller-Based Networking, REST APIs, and JSON — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | REST API: which HTTP verb maps to CRUD 'Create'? | POST. Exam tip: POST creates a new resource; the response often returns the newly created object with an assigned ID. |
| 2 | REST API: which HTTP verb maps to CRUD 'Read'? | GET. Exam tip: GET never modifies data — it only retrieves the current state of a resource. |
| 3 | REST API: which HTTP verb maps to CRUD 'Update'? | PUT (also sometimes PATCH for partial updates on real systems, but CCNA maps Update to PUT). Exam tip: PUT typically replaces the full resource. |
| 4 | REST API: which HTTP verb maps to CRUD 'Delete'? | DELETE. Exam tip: removes the specified resource; idempotent — repeating it has the same end result. |
| 5 | JSON array indexing — first element index number? | 0 (zero-indexed). Exam tip: the 'second' item in a JSON array is referenced with index [1], not [2]. |
| 6 | JSON vs XML vs YAML — which is most human-readable/indentation-based, used in Ansible? | YAML. JSON uses braces/brackets (machine + human friendly, widely used in REST APIs). XML uses tags (verbose). Exam tip: CCNA emphasizes JSON for REST API bodies. |
| 7 | Controller-based networking vs traditional networking — key architectural difference? | Controller-based separates control plane (centralized in controller) from data plane (distributed in devices); traditional networking manages control and data plane per-device via individual CLI. |
| 8 | Underlay vs Overlay in an SDN fabric | Underlay = physical network providing IP reachability between devices. Overlay = virtual/logical network (e.g., VXLAN tunnels) built on top of the underlay to carry traffic and policy. |
| 9 | Ansible — agent model and communication method? | Agentless; uses push model over SSH (or APIs). Control node pushes configuration to managed nodes on-demand when a playbook runs. |
| 10 | Puppet & Chef — agent model and communication method? | Both are agent-based and pull-based: an installed agent/client on each managed node periodically pulls configuration from a central master/server. |
| 11 | Cisco DNA Center — core function at a conceptual level? | Centralized SDN controller providing network automation (config/policy push via APIs), assurance (analytics/telemetry for health monitoring), and design/policy management — replaces per-device CLI management. |
| 12 | JSON key-value pair syntax example | {"name": "Gi0/1", "status": "up"} — keys and string values are in double quotes; key:value pairs are comma-separated inside curly braces {}. Arrays use square brackets [ ]. |

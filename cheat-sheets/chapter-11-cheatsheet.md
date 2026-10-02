## Chapter 11: Controller-Based Networking, REST APIs, JSON

### HTTP Verb → CRUD Mapping (heavily tested)
| HTTP Verb | CRUD Operation | Notes |
|---|---|---|
| POST | Create | Adds new resource |
| GET | Read | Retrieves data, no side effects |
| PUT | Update | Replaces/modifies existing resource |
| DELETE | Delete | Removes resource |

### Data Encoding Formats
| Format | Structure | Readability | Common Use |
|---|---|---|---|
| JSON | `{ }` objects, `[ ]` arrays, key:value | Good, machine-friendly | REST API bodies (CCNA focus) |
| XML | `<tag></tag>` | Verbose | Legacy/enterprise APIs, SOAP |
| YAML | Indentation-based, no brackets | Best for humans | Ansible playbooks, config files |

### JSON Structure Rules
- Objects: `{ "key": "value" }` — keys always in double quotes.
- Arrays: `[ item1, item2 ]` — zero-indexed; first element is `[0]`.
- Nesting: objects and arrays can contain other objects/arrays.
- Example: `interfaces[1].status` → second array element's `status` key.

### Controller-Based vs Traditional Networking
| Aspect | Traditional | Controller-Based (SDN) |
|---|---|---|
| Config method | Per-device CLI | Centralized via controller/API |
| Control plane | Distributed (each device) | Centralized (controller) |
| Data plane | Distributed | Distributed (devices still forward) |
| Scalability | Manual, slow | Automated, fast |
| Example | Standalone routers/switches | Cisco DNA Center + fabric |

### Fabric Concepts
- **Underlay**: Physical network providing basic IP reachability (routing between fabric nodes).
- **Overlay**: Virtual/logical network (e.g., VXLAN) built on top of underlay, carries tenant traffic + segmentation.
- **Fabric**: Combination of overlay + underlay + control plane (e.g., Cisco SD-Access) managed by a controller.

### Cisco DNA Center — Conceptual Capabilities
- **Automation**: Push configs/policy to devices via APIs (Intent-Based Networking).
- **Assurance**: Telemetry/analytics for proactive health monitoring.
- **Design & Policy**: Centralized network design, segmentation, and policy enforcement.

### Configuration Management Tools
| Tool | Agent? | Model | Protocol |
|---|---|---|---|
| Ansible | Agentless | Push | SSH/API |
| Puppet | Agent-based | Pull | HTTPS (agent-to-master) |
| Chef | Agent-based | Pull | HTTPS (client-to-server) |

### Common Exam Traps
- Confusing PUT (Update) with POST (Create).
- Miscounting JSON array index (arrays start at 0, not 1).
- Assuming Ansible requires an agent (it does not — Puppet/Chef do).
- Thinking overlay = physical and underlay = virtual (it's reversed: underlay is physical, overlay is virtual).

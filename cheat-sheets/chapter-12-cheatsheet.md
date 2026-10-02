# Chapter 12 Cheat Sheet: Full Exam Simulation & Time Management

## Exam Time Budget (120 minutes total)
| Segment | Time Allocation |
|---|---|
| Simlets/Simulations (2-3 items) | 20-30 minutes reserved upfront |
| Multiple-choice + drag-and-drop (~85-100 items) | Remaining ~90-100 minutes |
| Final review of flagged items | Use leftover minutes at end |

**Rule of thumb:** Don't spend more than ~60-90 seconds on any single MCQ on the first pass. If unsure, guess + flag, then move on.

## Domain Weights (200-301 Blueprint)
| Domain | Weight |
|---|---|
| 1.0 Network Fundamentals | 20% |
| 2.0 Network Access | 20% |
| 3.0 IP Connectivity | 25% |
| 4.0 IP Services | 10% |
| 5.0 Security Fundamentals | 15% |
| 6.0 Automation & Programmability | 10% |

**Study priority order (by weight):** IP Connectivity > Network Fundamentals = Network Access > Security Fundamentals > IP Services = Automation.

## Triage Strategy
1. Pass 1: Answer every quick MCQ immediately — don't overthink.
2. Flag anything uncertain, but always leave a best-guess answer selected first.
3. Skip full simlets on first pass if they threaten your MCQ time budget — flag and return.
4. Pass 2: Tackle flagged simlets/simulations using reserved 20-30 min block.
5. Pass 3: Use any remaining minutes to revisit flagged MCQs/drag-and-drop items.

## Drag-and-Drop Approach
- Do NOT drag randomly — identify the pattern first (e.g., subnet mask ↔ host count, protocol ↔ port number, term ↔ definition).
- Once the pattern is clear, place all matches in one efficient pass.
- If truly stuck, use elimination: place confident matches first, remaining items sort themselves.

## Simlet/Simulation Time Management
- Read the exact requirement before touching the CLI/topology.
- Configure only what's asked — extra configuration wastes time and risks errors.
- Verify with one targeted `show` command, not a full audit.
- Simlets may award partial credit — always attempt rather than skip entirely if time allows.

## Post-Exam (Practice Test) Analysis Workflow
1. Review full score breakdown by domain.
2. Cross-reference low-scoring domains against blueprint weight — prioritize weak + high-weight domains first (e.g., weak IP Connectivity > weak Automation).
3. Re-lab the specific weak topics, not just re-read theory.
4. Retake a fresh full-length practice exam (not the same one) to confirm improvement before scheduling the real exam.

## Testlet vs Simlet
| Type | Interactive? | Format |
|---|---|---|
| Testlet | No | Scenario + several standard MCQs |
| Simlet | Yes | Simulated device/topology requiring configuration or troubleshooting |

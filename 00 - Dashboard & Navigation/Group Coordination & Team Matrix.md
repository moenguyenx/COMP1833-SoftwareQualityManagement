# Group Coordination & Team Matrix

> [!IMPORTANT]
> The COMP1833 specification mandates teams of **4 to 5 students**. 
> - **Zero-Overlap Rule**: Each team member **MUST** select two distinct product functionalities (Part 2) and a unique ISO/IEC 25010 sub-topic (Part 4).
> - **Peer Review Pairing**: Each member must review another member's architectural blocks.

---

## 👥 Team Member Assignment Matrix (4 to 5 Students)

Below is the optimized allocation schema ensuring 100% compliance with course regulations:

| Role / Identifier | Name & Student ID | Part 2: Product Functionality I | Part 2: Product Functionality II | Part 4: ISO 25010 Sub-Topic | Part 2: Peer Reviewer For | Reviewed By |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Member 1 (Project Lead)** | `[Student Name 1]` | **F1**: Real-Time Emergency Patient Triage & Bed Dispatch | **F2**: AI Predictive Facility Maintenance & Sensor Alerting | **Performance Efficiency** (Time behaviour & Resource utilisation) | Member 2 | Member 5 (or 4) |
| **Member 2 (Architecture Lead)** | `[Student Name 2]` | **F3**: Multi-Party Clinical Collaboration & Instant Messaging | **F4**: Third-Party Service Provider Dispatch & Inventory Sync | **Security** (Confidentiality, Integrity & Accountability) | Member 3 | Member 1 |
| **Member 3 (SQA & SCM Lead)** | `[Student Name 3]` | **F5**: Patient Self-Service Portal & Privacy Management | **F6**: Gamified Patient Wellness & Reward Scheme Engine | **Usability** (Learnability, Accessibility & Operability) | Member 4 | Member 2 |
| **Member 4 (Test Lead)** | `[Student Name 4]` | **F7**: IoT Medical Sensor Telemetry Ingestion Engine | **F8**: Automated High-Availability Failover & State Backup | **Portability** (Adaptability, Installability & Replaceability) | Member 5 (or 1) | Member 3 |
| **Member 5 (Risk & Compliance Lead)** | `[Student Name 5]` *(if 5 members)* | **F9**: Patient Feedback & Continuous Service Improvement Loop | **F10**: Regulatory Compliance & Audit Trail Logging | **Maintainability** (Modularity, Analyzability & Testability) | Member 1 | Member 4 |

> [!NOTE]
> If your team consists of **4 students**, Member 5's topics can be merged or omitted; Member 1 to 4 cover Performance, Security, Usability, and Portability/Maintainability.

---

## 🔄 Peer Review Pairing Schedule (Part 2.2)

To satisfy the University of Greenwich peer review requirement, use a closed-loop review cycle:

```
[Member 1] ──reviews──► [Member 2] ──reviews──► [Member 3]
    ▲                                                │
    │                   [Member 5]                   ▼
    └────────────── reviews ◄─── reviews ───────── [Member 4]
```

- **Review Protocol**:
  1. Author submits Architectural Blocks draft by **Day 20**.
  2. Reviewer completes the [[03 - Part 2 - SQA & Architectural Blocks (Individual)/2.2 - Peer Review Methodology & Report Template|Formal Peer Review Report Form]] within 72 hours.
  3. Author applies constructive feedback, documents changes in an audit log, and both sign off.

---

## 🛠️ Group Deliverables RACI Matrix (Parts 1 & 3)

| Task / Section | Member 1 | Member 2 | Member 3 | Member 4 | Member 5 |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **1.1 Project Description & Problem Context** | **Accountable** | Consulted | Informed | Informed | Informed |
| **1.1 Architecture & Flow Diagrams** | Informed | **Responsible** | Consulted | Consulted | Informed |
| **1.2 Meeting Policy Document** | Consulted | Informed | **Responsible** | Informed | Informed |
| **1.3 Legal, Social, Ethical, Professional (LSEP)** | Informed | Informed | Informed | Informed | **Responsible** |
| **3.1 SQP: User Documentation Plan** | Informed | Consulted | **Responsible** | Informed | Informed |
| **3.1 SQP: Configuration Management (SCM)** | Informed | **Responsible** | Consulted | Informed | Informed |
| **3.2 SQP: Roles, Responsibilities & RACI** | **Accountable** | Informed | Informed | Informed | Consulted |
| **3.2 SQP: QA Resource Estimation & Cost of Quality** | Informed | Informed | Consulted | **Responsible** | Informed |
| **Final Assembly, Formatting & Turnitin Audit** | **Accountable** | Responsible | Responsible | Responsible | Responsible |

*Key: **R** = Responsible (does work), **A** = Accountable (approves/ensures delivery), **C** = Consulted (gives input), **I** = Informed (receives updates).*

---

## 🤝 Team Working Agreement & Code of Conduct

1. **Commitment**: All members agree to deliver drafts 5 days before internal deadlines to allow peer review and quality editing.
2. **Standard of Work**: Every section must meet **Level 7 (Master's level)** depth: clear definitions, critical evaluation of trade-offs, standard adherence, and complete citations.
3. **Communication**: Daily asynchronous check-ins on Microsoft Teams / WhatsApp; weekly synchronous meeting with formal minutes recorded as per [[02 - Part 1 - Project Planning (Group)/1.2 - Meeting Policy Document Guide & Policy Template|Meeting Policy]].
4. **Dispute Resolution**: If a conflict arises regarding content or workload, the team will follow the Escalation Pathway codified in the Meeting Policy document before approaching the Course Coordinator.

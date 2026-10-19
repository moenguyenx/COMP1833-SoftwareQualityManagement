# Case Study Deep Dive: Manchester Healthcare Entity (MHE) & SATZ

> [!NOTE]
> This document synthesizes every factual detail from the Coursework Appendix, translating clinical and operational challenges into actionable Software Quality Management (SQM) engineering requirements.

---

## 🏥 Context & Key Actors

- **The Client**: **Manchester Healthcare Entity (MHE)**  
  The regional governing body overseeing municipal healthcare delivery across Manchester, UK. Currently encumbered by fragile legacy systems and process silos.
- **The Vendor / Contractor**: **SATZ**  
  An enterprise Software Technology Company commissioned to engineer and deploy an AI-powered Healthcare Management software platform.
- **Key User Groups & Stakeholders**:
  1. **Patients**: Need intuitive self-service, timely access to care, transparency, privacy controls, and incentives (reward scheme).
  2. **Clinical & Administrative Staff**: Suffer from lack of training, opaque operational visibility, and disjointed communication.
  3. **Healthcare Facilities**: Physical clinics and hospitals that currently cannot maintain themselves; require automated facility tracking and IoT management.
  4. **Third-Party Service Providers**: Ambulances, medical transport, diagnostic laboratories, equipment contractors, and home care agencies lacking real-time collaboration.
  5. **Healthcare Regulators**: Care Quality Commission (CQC), NHS England, and the Information Commissioner's Office (ICO).

---

## 🔍 Root Cause Analysis of Past Failure (The "Ghost of the Previous Project")

The case study notes that MHE previously attempted an advanced software rollout that resulted in catastrophic failure:
- **Contractor Default**: The former firm overshot budget and schedule, collapsed financially ("folded"), and abandoned the initiative.
- **Zero Documentation**: Left MHE with an unusable software prototype containing *no architectural documentation, user manuals, or source code specs*.
- **Direct SQM Lesson**: This historical trauma explains why **Part 3 (Software Quality Plan)** is so heavily weighted in this coursework. SATZ must provide absolute guarantees around **Configuration Management**, **Traceability**, **Auditable Documentation**, and **Cost of Quality Estimation (IEEE 730-2014)**.

---

## ⚠️ Critical Operational Deficiencies & Architectural Countermeasures

| Case Study Observation | Operational Risk | Architectural & SQA Countermeasure |
| :--- | :--- | :--- |
| **No AI Integration & Zero Visibility** | Staff cannot forecast bed availability, triage bottlenecks, or resource depletion. | Real-time AI Operations Analytics Engine & Predictive Triage Dashboard. |
| **Facilities Cannot Maintain Themselves** | Unnoticed medical equipment failures, HVAC issues, power drops, room downtime. | IoT Sensor & Controller Telemetry Bus (MQTT/Kafka) feeding Predictive Maintenance AI. |
| **Clunky Web Form for Privacy Requests** | Slow response times, potential UK GDPR non-compliance, patient frustration. | In-App Real-time Privacy Management & Consent Self-Service Portal (OAuth2/RBAC). |
| **No Real-Time Provider Collaboration** | Delayed ambulance handoffs, duplicate lab orders, fragmented patient handovers. | Real-time WebSockets & Event-Driven Message Broker for multi-agency collaboration. |
| **Single Point of Failure (SPOF)** | MHE relies on one brittle legacy system; any downtime paralyzes regional healthcare. | Multi-Region Active-Active Cloud Architecture, Microservice Isolation & Automated Failover. |
| **Limited Staff Training & Patient Struggle** | High cognitive load, user rejection, medical input errors, wasted clinician hours. | Context-sensitive UI/UX, In-App Interactive Guidance, Comprehensive IEEE-compliant SQP Docs. |
| **Adoption Resistance** | Low digital engagement from traditional patient demographics. | Gamified Healthcare Reward Scheme (tokens/credits for preventive care, checkups, surveys). |
| **Sustainability & Continuous Improvement** | High carbon footprint, unmonitored energy spikes, static software that decays over time. | Cloud server auto-scaling, IoT smart power controllers, closed-loop telemetry analytics. |

---

## 🎯 Strategic Value Proposition of the SATZ Solution

The new system—provisionally titled **"SATZ Manchester HealthAI"**—must deliver:
1. **Clinical & Operational Safety**: Eliminating single points of failure, ensuring 99.999% availability for critical emergency routes.
2. **Data-Driven Automation**: Automated triage dispatch, automated equipment maintenance alerts, and seamless third-party scheduling.
3. **Regulatory Compliance by Design**: Adherence to UK GDPR, Data Protection Act 2018, Caldicott Principles, and NHS Data Security and Protection Toolkit (DSPT).
4. **Predictable Engineering Economics**: Applying IEEE 730-2014 quality planning to guarantee schedule integrity, configuration baselines, and transparent resource burn rates.

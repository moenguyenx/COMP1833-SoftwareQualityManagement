# Diagram 2: Software & Operational Process Flow (End-to-End Ingestion, AI & Dispatch)

> [!IMPORTANT]
> **Coursework Deliverable**: Part 1.1 Project Description Document (10 Marks).  
> This diagram illustrates the **Dynamic Operational Flow** of data, decision-making, and multi-agency coordination through the SATZ platform. It traces two complementary lifecycles:  
> 1. **Patient-Initiated Care & Self-Service Flow** (Booking -> Privacy Check -> AI Triage -> Department Routing or Nurse Review -> Reward Allocation).  
> 2. **IoT-Initiated Facility Predictive Maintenance Flow** (Sensor Telemetry -> Edge Gateway -> Rules & AI Anomaly Detection -> Alert & Automated Work Order -> Third-Party Contractor Dispatch).

---

## 🔄 End-to-End Software Flow Diagram (Mermaid)

```mermaid
sequenceDiagram
    autonumber
    actor Patient as 🧑 Patient (Mobile App)
    actor IoT as 📡 IoT Sensors / Controllers
    participant Edge as ⚡ Edge Gateway
    participant Gateway as 🛡️ API Gateway & WAF
    participant Privacy as 🔒 Consent & Privacy Broker
    participant Kafka as 📨 Kafka Event Stream
    participant AI as 🧠 AI Real-Time Optimizer
    participant Core as ⚙️ Clinical & Ops Microservices
    participant Staff as 👨‍⚕️ Clinical Ward Staff
    participant Contractor as 🚑 3rd-Party Provider (Ambulance/Maintenance)
    participant DB as 🗄️ Resilient DB & Audit Log
    participant Reward as 🎁 Gamified Reward Engine

    %% FLOW A: PATIENT SERVICE REQUEST & TRIAGE
    rect rgb(235, 245, 255)
    Note over Patient, Reward: SCENARIO A: Booking-Time AI Triage & Department Routing
    Patient->>Gateway: Submit Booking (Symptom Text, Consent)
    Gateway->>Privacy: Verify UK GDPR Consent & Privacy Preferences
    Privacy-->>Gateway: Consent Confirmed (Token Validated)
    Gateway->>Kafka: Publish "TriageRequestedEvent"
    Kafka->>AI: Consume Event for Real-Time Triage
    AI->>AI: Check Red-Flag Rules, Classify Symptoms to Department, Measure Confidence
    alt Red-flag symptom detected
        AI->>Core: Emergency Advice (999 or ED)
        Core->>Patient: Show Emergency Guidance
        Core->>Staff: Alert Triage Nurse
    else Confident result (0.80 or above)
        AI->>Core: Recommended Department (e.g., Respiratory)
        Core->>Patient: Offer Appointment Slot in Department
    else Vague input or low confidence
        AI->>Core: Escalate to Human (no AI result shown)
        Core->>Staff: Add Case to Triage Nurse Queue
        Staff-->>Core: Confirm Department or Call Patient Back
        Core->>Patient: Confirm Appointment or Call-back
    end
    Core->>DB: Persist Triage Record & Write Immutable Audit Record
    opt Patient transport requested by nurse
        Core->>Contractor: Request Patient Transport via WebSockets
        Contractor-->>Core: Acknowledge Dispatch ETA
    end
    Core->>Reward: Trigger Self-Service Engagement Event
    Reward->>Patient: Credit 50 "Manchester Health Points" (Reward Scheme)
    end

    %% FLOW B: IOT SENSOR PREDICTIVE FACILITY MAINTENANCE
    rect rgb(245, 240, 255)
    Note over IoT, DB: SCENARIO B: IoT Predictive Facility Maintenance & Alerting
    IoT->>Edge: Stream Sensor Telemetry (Autoclave Pressure / Temp)
    Edge->>Gateway: Forward Normalized Sensor Stream (MQTT over TLS)
    Gateway->>Kafka: Publish "FacilityTelemetryEvent"
    Kafka->>AI: Real-Time Stream Ingestion (Apache Flink)
    AI->>AI: Hard-Limit Rules and Predictive Model Detect Anomaly (Pre-failure Bearing Vibration)
    AI->>Core: Trigger "PreventativeMaintenanceAlert" (Severity: Critical)
    Core->>DB: Log Alert and Diagnostic Metric in TimescaleDB
    par Alerting and Work Order
        Core->>Contractor: Issue Automated Work Order to Maintenance Contractor
        Core->>Staff: Notify Estates Team and Ward Staff (Dashboard and SMS)
    end
    Contractor-->>Core: Work Order Accepted (Technician En Route)
    Contractor-->>Core: Report Finding (Real Fault or False Alarm) for Model Feedback
    end

    %% FLOW C: CONTINUOUS IMPROVEMENT & FEEDBACK LOOP
    rect rgb(240, 255, 240)
    Note over Patient, AI: SCENARIO C: Continuous Service Improvement & Retraining Loop
    Patient->>Gateway: Submit Post-Care Experience Feedback (1-5 Stars + Comments)
    Staff->>Gateway: Submit Shift Operational Efficiency Notes
    Gateway->>DB: Store Feedback & Incident Metrics
    DB->>AI: Nightly Batch Ingestion for Model Retraining & Accuracy Tuning
    end
```

---

## 📊 Detailed Narrative of Operational Stages (Level 7 Quality)

### Stage 1: Multi-Source Telemetry Ingestion & Privacy Verification
The operational flow begins at the edge. Patient interactions initiate via high-accessibility web or mobile endpoints, while physical facility assets stream telemetry at sub-second intervals:
- **UK GDPR Enforcement**: In compliance with the UK Data Protection Act 2018, every incoming transaction passes through the **In-App Privacy & Consent Broker**. If a patient has revoked consent for non-essential telemetry tracking, the system automatically sanitizes and anonymizes the payload prior to event publishing.
- **Protocol Normalization**: The Edge Gateway buffers and normalizes raw industrial sensor data (e.g., Modbus, BACnet, CoAP) into structured JSON payloads over **MQTT TLS 1.3**, preventing packet loss during local network instability.

### Stage 2: Event-Driven Decoupling via Apache Kafka
Rather than coupling the user interface directly to processing databases, incoming requests are published as strongly-typed events to an **Apache Kafka Event Bus**:
- **Benefits**: Decouples traffic spikes from backend processors, provides durable message buffering, and enables concurrent, asynchronous consumers (e.g., Clinical microservices, audit logger, analytics engine).

### Stage 3: AI Inference & Real-Time Operational Decisioning
The SATZ AI Engine operates concurrently on event streams:
- **AI Triage Routing**: Deterministic red-flag rules and a text classifier recommend a department from the symptoms the patient types at booking. The AI **never diagnoses**. If it is not confident, or the input is vague, the case is passed to a triage nurse, and any AI failure falls back to the nurse (fail-safe).
- **Predictive Facility Maintenance**: Fixed hard-limit rules always alert on unsafe readings, and time-series anomaly detection (e.g., Isolation Forests / LSTM autoencoders) detects vibrational or thermal drift in critical infrastructure (autoclaves, generators, ventilation) before hardware failure occurs. The platform raises alerts and work orders, and does not automatically shut down equipment.

### Stage 4: Synchronized Multi-Agency Dispatch & Collaboration
Addressing the case study's finding that *"there is no real-time collaboration among service providers"*:
- When an emergency or maintenance event is triggered, the **Application Microservices Layer** broadcasts bidirectional notifications simultaneously to ward workstations, mobile clinical devices, and third-party contractors (e.g., ambulance dispatchers, outsourced biomedical engineers) using secure **WebSockets**.
- Both parties acknowledge receipt, synchronizing status in real-time on a single shared operational dashboard.

### Stage 5: Gamified Adoption & Continuous Improvement Loop
Addressing MHE's mandate to encourage digital self-service and drive ongoing enhancements:
- **Reward Scheme Engine**: Successfully completed self-service actions (e.g., digital triage pre-checkin, attending preventive health screenings, completing follow-ups) trigger automated credit of "Health Points", redeemable for wellness subsidies or municipal benefits.
- **Continuous Feedback**: Post-service feedback from clinicians and patients is logged into the audit repository and ingested during automated retraining cycles, ensuring algorithms continuously adapt to Manchester's shifting clinical realities.

---

## 💡 How to Integrate Diagram 2 into Your Coursework Report

- **Pairing with Diagram 1**: While Diagram 1 provides the structural *spatial blueprint* (where components reside), Diagram 2 provides the *temporal dynamic narrative* (how data and events actually flow).
- **Referencing in Section 1.1**: Cite this diagram to demonstrate how the platform achieves real-time collaboration and eliminates the informational silos that crippled MHE's prior implementation.

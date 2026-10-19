# Diagram 2: Software & Operational Process Flow (End-to-End Ingestion, AI & Dispatch)

> [!IMPORTANT]
> **Coursework Deliverable**: Part 1.1 Project Description Document (10 Marks).  
> This diagram illustrates the **Dynamic Operational Flow** of data, decision-making, and multi-agency coordination through the SATZ platform. It traces two complementary lifecycles:  
> 1. **Patient-Initiated Care & Self-Service Flow** (Request -> Privacy Check -> AI Triage -> Clinical Dispatch -> Reward Allocation).  
> 2. **IoT-Initiated Facility Predictive Maintenance Flow** (Sensor Telemetry -> Edge Gateway -> AI Anomaly Detection -> Automated Work Order -> Third-Party Contractor Dispatch).

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
    Note over Patient, Reward: SCENARIO A: Patient Urgent Care Request & Automated Dispatch
    Patient->>Gateway: Submit Service Request (Symptoms, Location, Consent)
    Gateway->>Privacy: Verify UK GDPR Consent & Privacy Preferences
    Privacy-->>Gateway: Consent Confirmed (Token Validated)
    Gateway->>Kafka: Publish "PatientCareRequestedEvent"
    Kafka->>AI: Consume Event for Real-Time Triage Scoring
    AI->>AI: Evaluate Wait Times, Bed Capacity & Symptom Severity
    AI->>Core: Emit Optimized Allocation Plan (Priority: High, Ward: 3B)
    Core->>DB: Persist Triage State & Write Immutable Audit Record
    par Real-Time Multi-Agency Notification
        Core->>Staff: Push Urgent Alert to Ward Workstation (Bed Reserved)
        Core->>Contractor: Dispatch Ambulatory Transport via WebSockets
    end
    Staff-->>Core: Acknowledge Bed Acceptance
    Contractor-->>Core: Acknowledge Dispatch ETA (8 mins)
    Core->>Patient: Send Live Tracking & Arrival Instructions
    Core->>Reward: Trigger Self-Service Engagement Event
    Reward->>Patient: Credit 50 "Manchester Health Points" (Reward Scheme)
    end

    %% FLOW B: IOT SENSOR PREDICTIVE FACILITY MAINTENANCE
    rect rgb(245, 240, 255)
    Note over IoT, DB: SCENARIO B: IoT Predictive Facility Maintenance & Self-Healing
    IoT->>Edge: Stream Sensor Telemetry (Autoclave Pressure / Temp)
    Edge->>Gateway: Forward Normalized Sensor Stream (MQTT over TLS)
    Gateway->>Kafka: Publish "FacilityTelemetryEvent"
    Kafka->>AI: Real-Time Stream Ingestion (Apache Flink)
    AI->>AI: Detect Anomaly Pattern (Pre-failure Bearing Vibration)
    AI->>Core: Trigger "PreventativeMaintenanceAlert" (Severity: Critical)
    Core->>DB: Log Diagnostic Metric in TimescaleDB
    par Automated Facility Action
        Core->>IoT: Transmit Emergency Throttling Command to Controller
        Core->>Contractor: Issue Automated Work Order to Maintenance Contractor
        Core->>Staff: Notify Clinical Staff of Temporary Equipment Reroute
    end
    Contractor-->>Core: Work Order Accepted (Technician En Route)
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
- **Benefits**: Decouples traffic spikes from backend processors, guarantees zero message loss (persistence buffer), and enables concurrent, asynchronous consumers (e.g., Clinical microservices, audit logger, analytics engine).

### Stage 3: AI Inference & Real-Time Operational Decisioning
The SATZ AI Engine operates concurrently on event streams:
- **Triage Optimization**: Uses predictive machine learning models trained on historical patient throughput to calculate dynamic triage acuity scores, balancing emergency room queues and preventing clinical overload.
- **Predictive Facility Maintenance**: Employs time-series anomaly detection algorithms (e.g., Isolation Forests / LSTM autoencoders) to detect vibrational or thermal anomalies in critical infrastructure (autoclaves, MRI cooling, ventilation) before hardware failure occurs.

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

# Diagram 1: AI-Powered Healthcare System Architecture (C4 Model & High Availability)

> [!IMPORTANT]
> **Coursework Deliverable**: Part 1.1 Project Description Document (10 Marks).  
> **Requirement**: *"Please introduce a diagram to support your project description."*  
> This diagram represents the **Target Enterprise Architecture** for SATZ's transformation of Manchester Healthcare Entity (MHE). It directly addresses all clinical bottlenecks, IoT integration, AI analytics, and specifically **eliminates the legacy Single Point of Failure (SPOF)**.

---

## 📐 High-Level Architecture Diagram (Mermaid)

```mermaid
flowchart TB
    %% STYLING AND THEMES
    classDef clientStyle fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:#01579b;
    classDef iotStyle fill:#ede7f6,stroke:#512da8,stroke-width:2px,color:#311b92;
    classDef gatewayStyle fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#e65100;
    classDef serviceStyle fill:#e8f5e9,stroke:#388e3c,stroke-width:2px,color:#1b5e20;
    classDef aiStyle fill:#fce4ec,stroke:#c2185b,stroke-width:2px,color:#880e4f;
    classDef dataStyle fill:#efebe9,stroke:#5d4037,stroke-width:2px,color:#3e2723;
    classDef externalStyle fill:#f5f5f5,stroke:#616161,stroke-width:2px,color:#212121;
    classDef drStyle fill:#ffebee,stroke:#d32f2f,stroke-width:2px,stroke-dasharray: 5 5,color:#b71c1c;

    %% 1. CLIENT & USER LAYER
    subgraph Client_Layer ["1. Stakeholder Access Tier (Multi-Channel Web & Mobile)"]
        direction LR
        P_User["🧑 Patients\n(Mobile App & Self-Service Portal)"]:::clientStyle
        S_User["👨‍⚕️ Clinical & Ward Staff\n(Clinical Ops Workstation)"]:::clientStyle
        F_User["🏢 Facility Managers\n(Building & Asset Dashboard)"]:::clientStyle
        TP_User["🚑 3rd-Party Providers\n(Ambulance, Lab & Supply Portal)"]:::clientStyle
        A_User["⚖️ Regulators & CQC\n(Audit & Compliance Console)"]:::clientStyle
    end

    %% 2. IOT & EDGE TELEMETRY LAYER
    subgraph IoT_Layer ["2. IoT, Facility & Medical Telemetry Tier (Real-Time Sensors)"]
        direction LR
        Sensors["📡 Medical Wearables &\nBed Occupancy Sensors"]:::iotStyle
        Controllers["🎛️ Facility Controllers\n(HVAC, Power, Sterilization)"]:::iotStyle
        EdgeGW["⚡ Edge Gateway &\nProtocol Normalizer (MQTT/CoAP)"]:::iotStyle
        Sensors --> EdgeGW
        Controllers --> EdgeGW
    end

    %% 3. SECURITY & API GATEWAY LAYER
    subgraph Gateway_Layer ["3. Secure API Gateway & Identity Management Tier (DMZ)"]
        direction TB
        WAF["🛡️ Web Application Firewall (WAF) & DDoS Protection"]:::gatewayStyle
        APIGateway["🚪 API Gateway & Reverse Proxy (Kong / Envoy)"]:::gatewayStyle
        IAM["🔐 Identity & Access Management (OAuth2 / OIDC / NHS Login & CIS2)"]:::gatewayStyle
        PrivacyService["🔒 In-App UK GDPR Privacy & Consent Broker"]:::gatewayStyle
        WAF --> APIGateway
        APIGateway <--> IAM
        APIGateway <--> PrivacyService
    end

    %% Interconnection Clients & IoT to Gateway
    Client_Layer ==>|HTTPS / TLS 1.3 / mTLS| WAF
    EdgeGW ==>|MQTT over TLS / WebSockets| WAF

    %% 4. CORE MICROSERVICES LAYER
    subgraph Microservices_Layer ["4. Application Microservices Layer (Containerized Kubernetes Cluster)"]
        direction TB
        subgraph Group_Clinical ["Clinical & Patient Domains"]
            TriageService["🚑 AI Patient Triage &\nDepartment Routing Service"]:::serviceStyle
            SelfService["📱 Patient Self-Service &\nAppointment Service"]:::serviceStyle
            RewardService["🎁 Gamified Wellness &\nReward Scheme Engine"]:::serviceStyle
        end
        subgraph Group_Ops ["Operations & Logistics Domains"]
            FacilityService["🏢 Predictive Facility Maintenance\n& Asset Controller"]:::serviceStyle
            ProviderCollab["🤝 3rd-Party Real-Time\nCollaboration & Dispatch"]:::serviceStyle
            AuditService["📜 Immutable Audit Logger\n& Compliance Tracker"]:::serviceStyle
        end
    end

    APIGateway ==>|Internal gRPC & REST| Microservices_Layer

    %% 5. AI & REAL-TIME ANALYTICS ENGINE
    subgraph AI_Layer ["5. SATZ AI & Stream Analytics Engine"]
        direction TB
        Kafka["📨 Real-Time Event Bus\n(Apache Kafka / Event Streams)"]:::aiStyle
        StreamAnalytics["⚡ Stream Processing\n(Apache Flink / Spark)"]:::aiStyle
        ML_Models["🧠 AI Inference Models\n• Triage Department Routing\n• Facility Predictive Maintenance\n• Anomaly & Downtime Detection"]:::aiStyle
        Kafka --> StreamAnalytics --> ML_Models
    end

    Microservices_Layer <==>|Event Topics / Async Pub-Sub| Kafka
    ML_Models -.->|Real-time Insights & Triggers| Microservices_Layer

    %% 6. DATA PERSISTENCE & STORAGE TIER
    subgraph Data_Layer ["6. Resilient Data Persistence Tier (Active Cloud Region)"]
        direction LR
        PrimaryDB[("🗄️ Primary Relational Cluster\n(PostgreSQL HA / Multi-AZ)\nEncrypted at Rest (AES-256)")]:::dataStyle
        TimeSeriesDB[("📈 Time-Series IoT Store\n(InfluxDB / TimescaleDB)\nSensor Metrics & Logs")]:::dataStyle
        CacheCluster[("⚡ Distributed In-Memory Cache\n(Redis Sentinel Cluster)")]:::dataStyle
        DocStore[("📁 Encrypted Object Store\n(EHR Docs, Scans, S3/Blob)")]:::dataStyle
    end

    Microservices_Layer ==> Data_Layer

    %% 7. DISASTER RECOVERY & BACKUP (ELIMINATING SPOF)
    subgraph DR_Layer ["7. Disaster Recovery & Automated Backup Tier (Secondary Cloud Region / Zero SPOF)"]
        direction TB
        ReplicaDB[("🔄 Standby Geo-Replicated DB\n(Hot Standby / Automatic Failover)\nRTO < 5 min | RPO < 1 min")]:::drStyle
        ColdBackup[("💾 Air-Gapped Immutable\nDaily/Weekly Backups")]:::drStyle
    end

    PrimaryDB -.->|Asynchronous Geo-Replication| ReplicaDB
    PrimaryDB -.->|Automated Snapshot Pipeline| ColdBackup

    %% 8. EXTERNAL HEALTHCARE ECOSYSTEM
    subgraph External_Layer ["8. External Healthcare Interoperability Tier"]
        direction LR
        NHS_Spine["🏛️ NHS National Spine &\nEHR (HL7 FHIR API)"]:::externalStyle
        Ambulance_CAD["🚑 Regional Ambulance\nComputer-Aided Dispatch"]:::externalStyle
        Pathology_Labs["🔬 Diagnostic Labs &\nRegional Pharmacies"]:::externalStyle
    end

    Microservices_Layer <==>|Secure HL7 FHIR / HTTPS APIs| External_Layer
```

---

## 🏛️ Comprehensive Architectural Breakdown (Level 7 Academic Narrative)

### 1. Architectural Style & Design Justification
The SATZ Healthcare Platform transitions Manchester Healthcare Entity (MHE) away from an antiquated, monolithic architecture prone to catastrophic failure toward a **Decoupled, Event-Driven Microservices Architecture** deployed on a **Primary / Hot-Standby Cloud Foundation with Automated Geo-Redundancy**:
- **Fault Isolation**: Individual microservices (e.g., *Reward Scheme Service*) cannot crash core life-critical services (e.g., *Predictive Triage Service*).
- **Elimination of Single Point of Failure (SPOF)**: Addressing MHE's primary operational risk. By pairing an Active Primary Relational Cluster with an Asynchronously Geo-Replicated Hot Standby (Secondary Region), the architecture achieves a **Recovery Time Objective (RTO) < 5 minutes** and **Recovery Point Objective (RPO) < 1 minute**.
- **Elastic Scalability**: Healthcare demand spikes (e.g., winter flu epidemics or localized emergencies) are handled dynamically via Kubernetes Horizontal Pod Autoscalers (HPA).

### 2. Tier-by-Tier Component Specifications

| Tier | Key Components | Technical Implementation & Rationale |
| :--- | :--- | :--- |
| **1. Stakeholder Access Tier** | Responsive Web App, iOS/Android Mobile App, Clinical Tablet UI, Contractor Portal. | Built using TypeScript/React and React Native. Ensures **accessibility (WCAG 2.1 AA)** and multi-device usability across patients, ward staff, and external drivers. |
| **2. IoT & Facility Telemetry Tier** | Ward Bed Sensors, Environmental Thermostats, Power Controllers, Edge Gateways. | Ingests real-time telemetry via **MQTT over TLS 1.3**. Edge gateways perform protocol normalization and local caching in case of temporary network disruption. |
| **3. Security & API Gateway Tier** | Web Application Firewall (WAF), Kong API Gateway, OAuth2 / OIDC Identity Broker. | Centralizes authentication, rate limiting, and mTLS. Integrates with **NHS Login** (patients) and **NHS CIS2** (staff), and enforces the **UK Data Protection Act 2018 / UK GDPR** via dedicated In-App Privacy & Consent Brokers. |
| **4. Application Microservices Tier** | AI Triage & Routing, Patient Self-Service, Gamified Reward Engine, Facility Controller, Collaboration Service, Audit Logger. | Decoupled Spring Boot / Go microservices packaged in OCI-compliant Docker containers managed via Kubernetes. Enables independent updates, testing, and continuous deployment without hospital-wide downtime. |
| **5. AI & Stream Analytics Engine** | Apache Kafka, Apache Flink, Python ML Inference Services (PyTorch/Scikit-Learn). | Ingests event streams in real time. Runs the triage classifier and predictive maintenance algorithms to anticipate autoclave, HVAC, or scanner failures *before* they disrupt clinical workflows. |
| **6. Data Persistence Tier** | PostgreSQL High-Availability Cluster, TimescaleDB, Redis Cluster, Encrypted Object Storage. | Segregates operational relational data, high-velocity time-series sensor telemetry, and cached session data. Encrypted at rest using **AES-256** with HSM-managed keys. |
| **7. Disaster Recovery & Backup Tier** | Hot Standby Geo-Replica, Air-Gapped Immutable Snapshots. | Direct countermeasure to MHE's legacy SPOF vulnerability. Features automated health checks and DNS failover (Route 53 / Cloudflare). |
| **8. External Interoperability Tier** | NHS National Spine, Ambulance CAD, Regional Pharmacies. | Adheres to **HL7 FHIR (Fast Healthcare Interoperability Resources)** standards, guaranteeing compliant data exchange across external healthcare providers. |

---

## 💡 How to Use This Diagram in Your Coursework Report (Part 1.1)

1. **Figure Caption**: Label the diagram formally as `Figure 1: Target System Architecture of the SATZ AI-Powered Healthcare Management Platform for MHE`.
2. **Critical Commentary**: Emphasize how this architecture directly solves the three major historical weaknesses identified in the case study:
   - *Past Project Collapse*: Modular microservices ensure that if one component needs replacement, the entire platform does not fail.
   - *Single Point of Failure*: Highlight the split between Tier 6 (Primary Data) and Tier 7 (Geo-Replication & Automated Failover).
   - *Disjointed Communication*: Highlight Tier 4's *Provider Collaboration Service* coupled with Tier 5's *Kafka Event Bus*, enabling real-time multi-agency notifications.

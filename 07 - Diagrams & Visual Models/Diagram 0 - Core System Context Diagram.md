# Diagram 0: Core System Context Diagram (C4 Level 1 Conceptual Boundary)

> [!IMPORTANT]
> **Architectural Level**: **C4 Model — Level 1: System Context Diagram (Core System Boundary)**.  
> **Purpose**: This diagram precedes the High-Level System Architecture Diagram. It establishes the **strategic perimeter** of the SATZ AI-Powered Healthcare Management Platform, illustrating the core system, its operational boundaries, the five primary stakeholder groups, and external NHS/IoT systems.

---

## 🌐 Core System Context Diagram (Mermaid)

```mermaid
flowchart TB
    %% STYLING AND THEMES
    classDef coreStyle fill:#1e88e5,stroke:#0d47a1,stroke-width:3px,color:#ffffff,font-weight:bold;
    classDef personStyle fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#0d47a1;
    classDef externalStyle fill:#ede7f6,stroke:#4527a0,stroke-width:2px,color:#311b92;
    classDef legacyStyle fill:#ffebee,stroke:#c62828,stroke-width:2px,stroke-dasharray: 5 5,color:#b71c1c;

    %% TOP: HUMAN STAKEHOLDERS (PEOPLE)
    subgraph Stakeholders ["Human Stakeholders (Users & Regulators)"]
        direction LR
        P_Patient["🧑 Patients & Carers\n• Symptom-based triage routing\n• Appointments & rewards\n• Granular privacy control"]:::personStyle
        P_Staff["👨‍⚕️ Clinical & Ward Staff\n• Real-time ward visibility\n• Triage nurse review queue\n• Multi-agency messaging"]:::personStyle
        P_Facility["🏢 Facility Managers\n• Asset telemetry dashboard\n• Autonomous work orders\n• HVAC & plant monitoring"]:::personStyle
        P_Provider["🚑 3rd-Party Providers\n• Ambulance dispatch\n• Equipment contractors\n• Pathology lab sync"]:::personStyle
        P_Regulator["⚖️ Regulators (CQC / ICO)\n• Compliance audits\n• UK GDPR access logs\n• Algorithmic safety audit"]:::personStyle
    end

    %% CENTER: CORE SYSTEM (SYSTEM UNDER DESIGN)
    subgraph SystemBoundary ["Project Scope Boundary: Manchester Healthcare Transformation"]
        CorePlatform(["🏥 SATZ Manchester HealthAI Platform\n(Core Healthcare Management System)\n\n• Ingests multi-source healthcare telemetry\n• Routes patients to the right department (AI triage)\n• Drives predictive facility maintenance\n• Eliminates Single Point of Failure (SPOF)\n• Coordinates real-time multi-agency workflows\n• Administers gamified wellness reward scheme"]):::coreStyle
    end

    %% BOTTOM & SIDES: EXTERNAL ENTERPRISE & IOT SYSTEMS
    subgraph ExternalSystems ["External Enterprise, IoT & Regulatory Ecosystem"]
        direction LR
        Ext_IoT["📡 IoT Sensors & Controllers\n(Ward beds, autoclaves, HVAC,\nmedical telemetry devices)"]:::externalStyle
        Ext_NHS["🏛️ NHS National Spine & EHR\n(HL7 FHIR clinical records,\nGP summary records)"]:::externalStyle
        Ext_CAD["🚑 Regional CAD System\n(North West Ambulance Service\nComputer-Aided Dispatch)"]:::externalStyle
        Ext_Auth["🔐 NHS Login & Identity\n(NHS Login for patients, CIS2 for staff,\nOAuth2 / OIDC authentication)"]:::externalStyle
        Ext_Legacy["💾 Legacy MHE System\n(Decommissioned to read-only\narchive during data migration)"]:::legacyStyle
    end

    %% INTERACTIONS: STAKEHOLDERS TO CORE SYSTEM
    P_Patient <==>|"Requests care, views wait times,<br/>manages consent and earns points"| CorePlatform
    P_Staff <==>|"Manages triage, monitors bed state,<br/>coordinates clinical care"| CorePlatform
    P_Facility <==>|"Receives maintenance alerts,<br/>reviews equipment lifecycle"| CorePlatform
    P_Provider <==>|"Receives synchronized work orders<br/>and real-time dispatch routes"| CorePlatform
    P_Regulator -.->|"Inspects immutable audit logs,<br/>DPIA compliance and clinical safety"| CorePlatform

    %% INTERACTIONS: CORE SYSTEM TO EXTERNAL SYSTEMS
    Ext_IoT ==>|"High-velocity sensor telemetry<br/>and alert events via MQTT/TLS"| CorePlatform

    CorePlatform <==>|"Synchronizes clinical patient records<br/>via secure HL7 FHIR APIs"| Ext_NHS
    CorePlatform <==>|"Exchanges emergency dispatch ETA<br/>and trauma status via WebSockets"| Ext_CAD
    CorePlatform <==>|"Authenticates users and delegates<br/>role-based identities"| Ext_Auth
    Ext_Legacy -.->|"One-time historical patient data<br/>ingestion and cold backup archive"| CorePlatform
```

---

## 🏛️ Comprehensive Architectural Narrative (C4 Level 1 Rationale)

### 1.0 Why a Core System Context Diagram Precedes the Architecture Diagram
In software architecture engineering (Bass, Clements and Kazman, 2021; Brown, 2018), jumping straight into containers, microservices, and databases without first framing the **System Context** is an anti-pattern. 

The **Core System Context Diagram (C4 Level 1)** establishes the strategic boundaries of the project by explicitly declaring:
1. **What is INSIDE the Scope Boundary**: The *SATZ Manchester HealthAI Platform*—the unified, intelligent ecosystem commissioned to transform municipal healthcare.
2. **What is OUTSIDE the Scope Boundary**: Existing hospital hardware, national NHS backbones, external ambulance dispatchers, and legacy databases that SATZ must interoperate with but does not rebuild from scratch.
3. **The Human Actors**: The diverse human personas who interact with the system, highlighting their distinct clinical, operational, and regulatory needs.

---

### 2.0 Key Entities & Relational Breakdown

| Category | Entity Name | Nature of Interaction with the Core System |
| :--- | :--- | :--- |
| **Core System** | **SATZ Manchester HealthAI Platform** | The centralized cognitive management software responsible for AI triage, predictive facility maintenance, real-time collaboration, and high-availability operations. |
| **Human Actor** | **Patients & Carers** | Accesses care via mobile/web portals, manages granular privacy settings under UK GDPR, checks real-time appointment availability, and earns wellness rewards. |
| **Human Actor** | **Clinical & Ward Staff** | Gains real-time operational visibility into bed occupancy, reviews triage cases escalated by the AI, and coordinates multi-party patient handovers. |
| **Human Actor** | **Facility Managers** | Monitors real-time environmental status, HVAC stability, and autoclave pressures; receives automated work orders before equipment fails physically. |
| **Human Actor** | **3rd-Party Providers** | Private ambulance contractors, outsourced medical equipment technicians, and diagnostic laboratories receiving synchronized dispatch and inventory updates. |
| **Human Actor** | **Regulators (CQC / ICO)** | Audits immutable access logs, verifies algorithmic fairness, and monitors compliance with the Data Protection Act 2018. |
| **External System** | **IoT Sensors & Controllers** | Hardware sensors streaming high-frequency telemetry (pressure, vibration, temperature, vitals) and edge controllers. |
| **External System** | **NHS National Spine & EHR** | The statutory UK healthcare backbone providing electronic health records via standardized HL7 FHIR APIs. |
| **External System** | **Regional Ambulance CAD** | North West Ambulance Service Computer-Aided Dispatch synchronizing real-time emergency transport and arrival ETAs. |
| **External System** | **NHS Login & Identity Provider** | UK identity services: NHS Login for patients and NHS CIS2 for staff authentication. |
| **External System** | **Legacy MHE System** | The fragile, monolithic legacy application being phased out. Relegated to a read-only historical archive, permanently eliminating the Single Point of Failure (SPOF). |

---

## 💡 How to Position This Diagram in Your Coursework (Part 1.1)

In your **Project Description Document (Section 1.1)**, structure your diagrams logically:
1. **First: [Diagram 0 - Core System Context Diagram](file:///P:/PersonalFiles/Academic/Greenwich/Academic/COMP1833-SQM/07%20-%20Diagrams%20&%20Visual%20Models/Diagram%200%20-%20Core%20System%20Context%20Diagram.md)**  
   *Caption: "Figure 1: Core System Context Diagram (C4 Level 1) of the SATZ Manchester HealthAI Platform, illustrating system perimeter, stakeholder interactions, and external integrations."*  
   *Purpose: Introduces the high-level boundary, external actors, and NHS integrations.*
2. **Second: [Diagram 1 - Healthcare System Architecture](file:///P:/PersonalFiles/Academic/Greenwich/Academic/COMP1833-SQM/07%20-%20Diagrams%20&%20Visual%20Models/Diagram%201%20-%20Healthcare%20System%20Architecture.md)**  
   *Caption: "Figure 2: High-Level System Architecture (C4 Level 2) illustrating multi-tier containerization, microservice decoupling, Kafka streaming, and geo-replicated disaster recovery."*  
   *Purpose: Zooms inside the core system box to show microservices, databases, and failover.*
3. **Third: [Diagram 2 - Software & Operational Flow](file:///P:/PersonalFiles/Academic/Greenwich/Academic/COMP1833-SQM/07%20-%20Diagrams%20&%20Visual%20Models/Diagram%202%20-%20Software%20&%20Operational%20Flow.md)**  
   *Caption: "Figure 3: Software & Operational Process Flow Diagram illustrating end-to-end data ingestion, AI triage, automated dispatch, and reward distribution."*  
   *Purpose: Demonstrates the dynamic temporal execution and data flows across the system.*

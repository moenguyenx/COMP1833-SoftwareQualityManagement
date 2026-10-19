# Level 7 Master's Academic Writing Standards & Critical Thinking

> [!IMPORTANT]
> **Academic Context**: University of Greenwich — Level 7 (MSc / Postgraduate).  
> **Coursework Directive (Page 4)**: *"This is a level seven Degree coursework and therefore, as well as demonstrating that you have learnt some facts or skills, you are being assessed on your ability to research, think, and reason and then articulate your findings and conclusions."*  
> **Rubric Anchor (D1 & D4)**: Scoring 80–100% demands transitioning from purely *descriptive* writing to *evaluative, evidence-backed synthesis*.

---

## 🧠 The Bloom's Taxonomy Paradigm: Level 6 vs Level 7

```
                     BLOOM'S TAXONOMY FOR POSTGRADUATE WRITING
┌─────────────────────────────────────────────────────────────────────────────────┐
│ LEVEL 7 (Postgraduate / MSc) : EVALUATE & SYNTHESIZE                            │
│ • Weighing contradictory trade-offs (e.g., latency vs encryption overhead)     │
│ • Justifying why standard A was tailored rather than standard B                 │
│ • Critiquing limitations of your own design and proposing concrete mitigations │
├─────────────────────────────────────────────────────────────────────────────────┤
│ LEVEL 6 (Undergraduate / BSc) : APPLY & ANALYZE                                 │
│ • Applying a textbook formula or drawing standard UML diagrams                 │
│ • Explaining what an architecture block does                                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│ LOWER LEVELS (Failing / Poor) : REMEMBER & DESCRIBE                             │
│ • Summarizing what Git is, defining what a hospital is, or copying Wikipedia    │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## ⚖️ The "Descriptive Trap" vs "Critical Evaluation"

Examine these two approaches to the same coursework topic:

### ❌ Descriptive (BSc Level / Grade: 45–55%)
> *"We used Git for our software configuration management. Git is a distributed version control system that lets people make branches. We also had a meeting policy where we met once a week on Teams to discuss our progress. If someone missed a meeting, we asked them why."*
> **Examiner Feedback**: Pure description. No academic grounding, no reflection on risk, no justification of why this branching model was chosen over alternatives, no reference to standards.

### ✅ Evaluative & Evidence-Backed (MSc Level 7 / Grade: 85–95%)
> *"To mitigate the institutional vulnerability exposed during MHE's previous software procurement—where vendor insolvency resulted in an undocumented and orphaned codebase—SATZ tailors IEEE Std 730-2014 Clause 5.3 by establishing an auditable Gitflow configuration baseline. While Trunk-based development offers rapid delivery velocity, a strict Gitflow branching model was deliberately selected to enforce cryptographic commit signing and dual peer-review quality gates prior to integration. This architectural constraint introduces an estimated 8% overhead in lead time but reduces regression defects by up to 35% in safety-critical deployments (Pressman and Maxim, 2020), directly addressing MHE’s need for verifiable software stability."*
> **Examiner Feedback**: Exceptional synthesis. Contextualized to the case study, supported by recognized standard (IEEE 730), critiques trade-offs (velocity vs stability), and provides quantitative justification with literature citation.

---

## 🏛️ The 4-Part Structure of an Evaluative Level 7 Argument (P-E-E-E)

When writing any paragraph across Parts 1 to 5, apply the **P-E-E-E Framework**:

1. **Point (Proposition)**:
   - Make a clear, assertive claim regarding software quality, architecture, or governance.
   - *Example: "Decoupling the Predictive Triage microservice from the persistent database via an in-memory Redis cache is essential to maintain high-acuity responsiveness."*
2. **Evidence (Literature or Standard Citation)**:
   - Support the claim using IEEE/ISO standards, case study data, or software engineering scholarship.
   - *Example: "In high-throughput clinical environments, synchronous relational database queries introduce catastrophic thread starvation under unexpected casualty surges (Bass et al., 2021; ISO/IEC 25010 Clause 4.2.1)."*
3. **Evaluation (Critical Analysis of Trade-offs)**:
   - Analyze the counter-argument, cost, or operational penalty.
   - *Example: "Although introducing an in-memory caching layer increases infrastructure expenditure and introduces transient cache-invalidation risks, the reduction in p99 read latency from 450ms to 18ms outweighs the operational overhead."*
4. **Execution / Synthesis (Application to MHE)**:
   - Close the loop by showing how this directly resolves a specific MHE case study constraint.
   - *Example: "This directly protects Manchester clinicians from workstation latency lag during mass casualty triage scenarios."*

---

## 📝 Golden Rules for Master's Academic Style

1. **Third-Person Objective Perspective**:
   - Prefer: *"The proposed architecture implements..."*, *"The SQA team established..."*, *"The evidence indicates..."*
   - Avoid: *"I think that..."*, *"We did this because we liked..."*
2. **Hedging & Epistemic Caution**:
   - In academic writing, avoid absolute dogmatism (*"This system will never fail"*).
   - Use nuanced epistemic markers: *"The implementation significantly minimizes the probability of single points of failure..."*, *"Empirical evidence suggests that..."*
3. **Explicit Cross-Referencing**:
   - Always connect text to figures and tables: *"As delineated in Table 3.2, the RACI matrix designates the Clinical Safety Officer as Accountable for algorithmic hazard sign-off..."*

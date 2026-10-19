# Final Pre-Submission Quality Audit Checklist

> [!IMPORTANT]
> Complete this quality audit before uploading your final Group and Individual PDF submissions to Turnitin / Moodle. Every item corresponds to critical criteria from the **University of Greenwich Assessment Rubric**.

---

## 🔍 Pre-Flight Quality Audit Matrix

### 1. General & Administrative Verification
- [ ] **Student Identity**: Full names and Student ID numbers are clearly listed on the cover page.
- [ ] **Deadline Check**: Submitted prior to **2nd December 2026, 5:00 PM UK Time**.
- [ ] **File Format**: Exported as clean, selectable PDF (not image scans) formatted in standard A4 with 1-inch margins and clear typography (11–12pt body text, 1.5 line spacing).
- [ ] **Plagiarism & AI Statement**: Verified that all text represents original academic analysis; any AI assistance was used strictly for research/outlining and no unreferenced AI text is present.

---

### 2. Group Deliverables Audit (Parts 1 & 3 — 40 Marks)

#### Part 1: Project Planning (20 Marks)
- [ ] **Section 1.1 Project Description**:
  - [ ] Operational problem in Manchester clearly articulated.
  - [ ] Role of SATZ and Manchester Healthcare Entity (MHE) defined.
  - [ ] **Figure 1 (System Architecture)** is embedded, high-resolution, captioned, and cross-referenced in the text.
  - [ ] **Figure 2 (Software & Operational Flow)** is embedded, captioned, and cross-referenced.
  - [ ] Explicitly addresses the elimination of the legacy Single Point of Failure (SPOF).
- [ ] **Section 1.2 Meeting Policy Document**:
  - [ ] Specifies meeting types, frequencies, and communication mediums.
  - [ ] Formal Quorum (e.g., 75%) and voting protocols defined.
  - [ ] Standing 5-stage agenda provided.
  - [ ] 4-stage non-performance escalation pathway clearly established.
  - [ ] Ratification table with team signatures/dates included.
- [ ] **Section 1.3 LSEP Analysis**:
  - [ ] **Legal**: UK Data Protection Act 2018 & UK GDPR (Article 9, DPIA, Article 22 CDSS).
  - [ ] **Caldicott**: Operationalization of the 8 Caldicott Principles.
  - [ ] **Social**: Greater Manchester digital divide, WCAG 2.1 AA accessibility, staff training deficit.
  - [ ] **Ethical**: Algorithmic bias in triage models, sensor surveillance vs privacy, gamification ethics.
  - [ ] **Professional**: BCS Code of Conduct (Public interest, competence, integrity).

#### Part 3: Software Quality Plan (IEEE 730-2014) (20 Marks)
- [ ] **Page Length Rule**: SQP is **strictly no less than three (3) pages** of high-density tailored text.
- [ ] **Section 3.1 Documentation & SCM**:
  - [ ] Stakeholder documentation taxonomy defined (Patients, Clinicians, Facility, Providers).
  - [ ] Docs-as-code and readability criteria specified.
  - [ ] SCM baseline strategy (Functional, Allocated, Developmental, Product) detailed.
  - [ ] Gitflow branching rules, branch protections, and commit signing codified.
  - [ ] Change Control Board (CCB) composition and change request lifecycle defined.
- [ ] **Section 3.2 Management & Resources**:
  - [ ] SQA organizational independence (reporting to CTO) clearly established.
  - [ ] Detailed role descriptions and complete RACI matrix provided.
  - [ ] Quantitative SQA effort estimation (28% of total PM) calculated via COCOMO II.
  - [ ] SQA tooling budget itemized.
  - [ ] Cost of Quality (CoQ) model (Prevention, Appraisal, Failure) rigorously articulated.

---

### 3. Individual Deliverables Audit (Parts 2, 4 & 5 — 60 Marks)

#### Part 2: SQA & Architecture (20 Marks)
- [ ] **Zero Overlap**: Functionality I and II are completely unique to this team member.
- [ ] **Section 2.1 Architectural Blocks**:
  - [ ] Clear block diagrams showing subsystems, APIs, and caches for both functionalities.
  - [ ] Strongly-typed data structures (JSON schemas, DDL, or TypeScript) provided with field-level constraints.
  - [ ] SQA justification explaining how the design improves safety, modularity, and fault tolerance.
- [ ] **Section 2.2 Peer Review Report**:
  - [ ] Review conducted on a peer's architectural blocks using IEEE Standard 1028-2008.
  - [ ] Review metadata and executive summary completed.
  - [ ] Defect logging register contains at least 3–4 specific defects (DEF-01 to DEF-04) categorized by severity.
  - [ ] Qualitative evaluation and author sign-off included.

#### Part 4: SRS & Use Cases (20 Marks)
- [ ] **Selected Sub-Topic**: Selected one of the 5 ISO 25010 topics (Performance, Security, Usability, Portability, Maintainability) with no group overlap.
- [ ] **Section 4.1 SRS**:
  - [ ] Two distinct, fully formulated SMART requirements with formal RFC 2119 keywords.
  - [ ] Explicit quantitative verification metrics (e.g., latency, capacity, test coverage).
  - [ ] Direct operational rationale connected to the MHE case study.
- [ ] **Section 4.2 Use Cases**:
  - [ ] Two complete Cockburn-style use case specification tables.
  - [ ] Includes primary/secondary actors, triggers, preconditions, main success scenarios, and alternative flows.
  - [ ] Direct traceability link validating the requirements in Section 4.1.

#### Part 5: Black Box Testing & Risk Management (20 Marks)
- [ ] **Section 5.1 Black Box Testing**:
  - [ ] Directly tests the two functionalities defined in Part 2.1.
  - [ ] Rigorous application of Equivalence Partitioning (valid and invalid classes).
  - [ ] Rigorous application of Boundary Value Analysis (on boundary, just below, just above).
  - [ ] Test execution table includes Test ID, Inputs, Expected Results, Actual Results, and Pass/Fail status.
  - [ ] Critical analysis connects testing defects to the risks in Section 5.2.
- [ ] **Section 5.2 Product Risk Management**:
  - [ ] Identifies two specific, high-consequence product risks derived from the functionalities/test findings.
  - [ ] Pre-control quantitative risk scoring using ISO 31000 5x5 matrix (Likelihood x Impact).
  - [ ] Three tiers of controls implemented for each risk: Preventative, Detective, and Corrective.
  - [ ] Post-control residual risk evaluated and proven to satisfy tolerable safety levels.

---

### 4. Referencing & Scholarship Audit (Rubric D5)
- [ ] **Reference Style Consistency**: Exclusively Cite Them Right Harvard OR IEEE style used throughout (no mixing).
- [ ] **Core Standards Cited**: IEEE 730-2014, ISO/IEC 25010, ISO 31000, IEEE 1028, and UK Data Protection Act 2018 are cited in-text and present in the bibliography.
- [ ] **Zero Orphan References**: Every entry in the reference list is cited at least once in the body text.
- [ ] **Academic Depth**: Sufficient peer-reviewed books, journals, and standards cited (15–25 for Group, 8–12 for Individual).

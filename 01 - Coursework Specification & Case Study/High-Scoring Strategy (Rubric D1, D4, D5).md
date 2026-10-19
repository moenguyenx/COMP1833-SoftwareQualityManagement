# High-Scoring Strategy: Securing 80–100% (Exceptional Level 7)

> [!IMPORTANT]
> The University of Greenwich assesses this MSc coursework against three primary rubric dimensions: **D1 (Knowledge & Critical Understanding)**, **D4 (Professional Communication & Presentation)**, and **D5 (Academic Referencing & Scholarship)**. Below is the blueprint for reaching the 80–100% band across all parts.

---

## 🏆 Assessment Rubric Analysis (Page 5 of Coursework Specification)

```
                            GRADE BOUNDARIES & EXPECTATIONS
┌────────────────────────────────────────────────────────────────────────────────────────┐
│  80–100% (Exceptional) : Professional, publishable standard. Deep critique & synthesis.│
├────────────────────────────────────────────────────────────────────────────────────────┤
│  70–79%  (Excellent)   : Thorough knowledge, robust methodology, full referencing.      │
├────────────────────────────────────────────────────────────────────────────────────────┤
│  60–69%  (Very Good)   : Clear understanding, sound arguments, standard academic style.│
├────────────────────────────────────────────────────────────────────────────────────────┤
│  50–59%  (Good)        : Basic competence, mostly descriptive, minimal critical depth. │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔑 Dimension 1: Knowledge & Critical Understanding (D1)

### How to Move from "Good / Very Good" (50–69%) to "Exceptional" (80–100%)

| Average / Descriptive Work (50–65%) | Exceptional Level 7 Work (80–100%) |
| :--- | :--- |
| Simply defining what an architectural block is. | Critically analyzing architectural styles (Microservices vs Monolith vs Event-Driven) in terms of latency, fault tolerance, and SPOF mitigation for healthcare environments. |
| Copying standard IEEE 730 clause headings without context. | **Tailoring** IEEE 730-2014 to a high-risk medical AI system, justifying why certain clauses are prioritized (e.g., SCM and verification) to avoid past contractor failures. |
| Stating "we will test the login page with valid and invalid inputs." | Applying formal **Equivalence Partitioning** and **Boundary Value Analysis** tables with explicit 2-value and 3-value boundary justification, error guessing, and ISO 31000 risk calculations. |
| Listing standard ISO 25010 characteristics generically. | Formulating precise, quantifiable SMART metrics (e.g., *p99 latency < 250ms under 10,000 concurrent sensor feeds*) tied to specific sub-characteristics. |

### Golden Rules for Level 7 Knowledge:
1. **Never Make Unsubstantiated Claims**: Every design choice must be justified with technical rationale or literature citation (e.g., Sommerville 2020; Pressman and Maxim 2020).
2. **Explicitly Address Past Project Failure**: Continuously show how your SQA procedures directly prevent the contractor collapse that damaged MHE previously.
3. **Use Formal Standards Notation**: Refer to clauses by number (e.g., *IEEE 730-2014 Clause 5.3 Software Configuration Management*, *ISO/IEC 25010:2011 Clause 4.2.1 Time Behaviour*).

---

## ✍️ Dimension 4: Professional Communication & Presentation (D4)

### Standards of Presentation for Master's Submissions:
- **Consistent Document Hierarchy**: Use clear decimal heading levels (1.0, 1.1, 1.1.1).
- **Professional Visual Assets**: Never use hand-drawn or blurry screenshots. Use vector diagrams, high-resolution SVG/PNG exports from Mermaid, with explicit figure numbering (`Figure 1: SATZ System Architecture`) and textual cross-referencing.
- **Informative Tables**: Use bordered, shaded tables with header rows for complex comparisons, test cases, and risk registers.
- **Academic Tone**: Third-person formal passive/active mix (*"The proposed architecture implements..."* rather than *"I made this diagram because..."*). Avoid conversational slang or superficial enthusiasm.

---

## 📚 Dimension 5: Academic Referencing & Scholarship (D5)

### Reaching "Evidence of Determining Extensive List of Outstanding Resources":
- **Breadth of Sources**: Aim for **15–25 high-quality citations** across the group report and **8–12 per individual report**.
- **Source Hierarchy**:
  1. *International Standards*: IEEE 730-2014, ISO/IEC 25010, ISO 31000, IEEE 1028, IEEE 829.
  2. *Statutory & Regulatory Frameworks*: UK Data Protection Act 2018, UK GDPR, Caldicott Principles 2020, Medical Devices Regulations (MDR 2002 / MHRA AI guidance).
  3. *Foundational Textbooks*: Pressman & Maxim (Software Quality), Sommerville (Software Engineering), O'Regan (Concise Guide to SQA).
  4. *Peer-Reviewed Academic Journals*: IEEE Transactions on Software Engineering, ACM Computing Surveys, Journal of Medical Internet Research.
- **Flawless Formatting**: Use Cite Them Right Harvard or IEEE consistently. No broken URLs, missing author names, or ambiguous dates.

> [!TIP]
> Visit the pre-built reference library in [[08 - Academic Writing & Citation Masterclass/Academic Bibliography & Reference Library|Academic Bibliography]] to copy verified, pre-formatted Harvard and IEEE references directly into your work!

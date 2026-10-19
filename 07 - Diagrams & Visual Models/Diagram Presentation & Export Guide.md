# Diagram Presentation & Export Guide

> [!TIP]
> This guide outlines how to view, export, and embed both coursework diagrams into your Microsoft Word or PDF submission documents to achieve maximum marks under **Criterion D4 (Professional Communication & Presentation)**.

---

## 🖥️ Viewing Diagrams in Obsidian

Obsidian supports Mermaid diagrams out of the box!
- **Live Preview / Reading Mode**: Switch Obsidian to "Reading View" (top right book icon or `Ctrl + E`) to render both `Diagram 1` and `Diagram 2` as interactive, scalable vector graphics.
- **Zoom & Pan**: You can click and zoom into diagrams directly within Obsidian.

---

## 📤 Exporting High-Resolution Images for Word / PDF Reports

To paste these diagrams into your coursework submission document (Microsoft Word or LaTeX), follow any of these simple methods:

### Method 1: Using Mermaid Live Editor (Recommended for Crisp Vector Output)
1. Open [[07 - Diagrams & Visual Models/Diagram 0 - Core System Context Diagram|Diagram 0]], [[07 - Diagrams & Visual Models/Diagram 1 - Healthcare System Architecture|Diagram 1]], or [[07 - Diagrams & Visual Models/Diagram 2 - Software & Operational Flow|Diagram 2]].
2. Copy the code block inside the ` ```mermaid ... ``` `.
3. Go to [Mermaid Live Editor](https://mermaid.live).
4. Paste the code into the left editor pane.
5. In the top-right corner of Mermaid Live:
   - Click **Download PNG** (choose 2x or 3x scale for crisp printing).
   - Or click **Download SVG** (infinite resolution vector format, natively supported in Microsoft Word 2016+).

### Method 2: Screenshotting Directly from Obsidian
1. In Obsidian, switch to **Reading Mode** (`Ctrl + E`).
2. Use Windows Snipping Tool (`Win + Shift + S`) to capture the rendered diagram at high resolution.
3. Paste directly into your document.

---

## 📝 Best Practices for Academic Formatting in Word

1. **Figure Numbering & Captions**:
   - Every diagram must have a formal caption placed **below** the figure.
   - Example:
     > **Figure 1**: *Core System Context Diagram (C4 Level 1) of the SATZ Manchester HealthAI Platform, illustrating system perimeter, stakeholder interactions, and external integrations.*
     > 
     > **Figure 2**: *Target High-Level System Architecture (C4 Level 2) illustrating multi-tier containerization, microservice decoupling, Kafka streaming, and geo-replicated disaster recovery.*
     > 
     > **Figure 3**: *Sequence and Software Flow Diagram of End-to-End Operational Triage, IoT Predictive Maintenance, and Gamified Continuous Improvement.*

2. **In-Text Cross Referencing**:
   - Never insert a diagram without referencing it in the text.
   - Good academic phrasing:
     > *"As illustrated in Figure 1, the system perimeter establishes clear demarcations between the core SATZ platform and external NHS Spine backbones..."*
     > *"As detailed in Figure 2, the proposed architecture separates client interactions from data persistence via an event-driven microservices topology..."*
     > *"The temporal sequence of emergency bed allocation is traced in Figure 3, highlighting the asynchronous event stream..."*

3. **Page Placement**:
   - Ensure the diagram is centered and takes up sufficient width (e.g., 80% to 100% of the text width) so that labels and arrows are legible when printed or viewed at 100% zoom.

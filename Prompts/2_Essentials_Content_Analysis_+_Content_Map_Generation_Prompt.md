# Unified Content‑Map Generation & Analysis Prompt

## 0  Source Materials (OneDrive, read‑only)

All mandatory files reside in the project’s OneDrive folder (read‑only):

`https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g`

| Purpose                                | **Exact File Name**                       |
| -------------------------------------- | ----------------------------------------- |
| Course structure (8‑module outline)    | **Essentials_course_structure.md**        |
| Learning gap, goal & objectives        | **Marketo_Essentials_Learning_Design.md** |
| Prompt‑module definitions              | **ai_prompt_modules_minimal.md**          |
| Authoring instructions for content map | **Content_Map_Instructions_v3.md**        |
| Target‑audience personas               | **Adobe_Sellers_Learner_Personas.md**     |

If any file above is missing or unreadable, invoke the **Halt & Report** rule.

---

## 1  Global Instructions

| Requirement     | Details                                                          |
| --------------- | ---------------------------------------------------------------- |
| **Language**    | Use British English throughout.                                  |
| **Memory**      | Clear any previous cache/memory before execution.                |
| **Tone**        | Clear, concise, instructional; calibrated to the target persona. |
| **Bloom Focus** | *Remember* level (unless otherwise specified in objectives).     |
| **Assessment**  | End‑of‑course quiz (plus module‑level checks as generated).      |

---

## 2  Pre‑Flight Validation

1. **Required attachments** — all five files listed in Section 0 must be present **with the exact names shown**.  
2. **Halt & Report** — if any file is missing or unreadable, output a **single bullet list** naming the unavailable items and **stop processing**.

---

## 3  Core Data to Extract & Lock

| Source                              | Must Be Used *Verbatim*                                                                       |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| **Learning Gap, Goal & Objectives** | Insert exactly as written from *Marketo_Essentials_Learning_Design.md*.                       |
| **8‑Module Course Structure**       | Extract from *Essentials_course_structure.md*.                                                |
| **Target Audience / Persona**       | Derive role, needs, experience level and context from *Adobe_Sellers_Learner_Personas.md*.    |

---

## 4  AI Prompt Modules (Invoke as Needed)

- **Learning_Activity_Generator_Module** – creates both formative activities **and** summative assessments  
- **Learning_Asset_Module** – asset types & formats  
- **Pedagogy_Module** – validate objectives & scaffolding  
- **Accessibility_Module** – WCAG, alt‑text, captions, inclusive design  
- **Tone_of_Voice_Module** – keep persona‑appropriate tone  
- **Visual_Style_Module** – clean, accessible, corporate look  
- **Learning_Theories_Checklist_Module** *(optional)* – alignment (Bloom, Gagné, SOLO, etc.)  
- **Cognitive_Keyword_Watchlist_Module** *(optional)* – highlight cognitive/emotional load cues  

*The combined remit of the Learning_Activity_Generator_Module covers detailed assessment design, so a standalone **Assessment_Design_Module** is not required.*

---

## 5  Execution Sequence

1. **Validate attachments & mandatory fields** (Section 2).  
2. **Expand topic‑intent statements** where required.  
3. **Generate & validate** gaps, goals, objectives and outcomes (via *Learner_Outcomes_Module*).  
4. **Map** extracted content to the eight modules.  
5. **Align** every item to instructional‑theory tags (Bloom, Gagné, Kirkpatrick, ARCS).  
5a. **Run Accessibility_Module** on all generated assets; halt if WCAG 2.2 AA criteria are not met.  
6. **Generate activities/assessments** with *Learning_Activity_Generator_Module*:  
   - **Summary** for Layer 1 table.  
   - **Detail** for Layer 2 appendix (include outputs from *Differentiation_Scaffolding_Module*, *Accessibility_Module*, *Misconception_Check_Module*).  
7. **Assemble/export** outputs as `.docx` per Section 6 standards *(accepts optional `module_id` parameter to regenerate a single module only)*.

---

## 6  Output Specification

### 6.1  Header (once per document)

Course Title | Generation Date (timestamp) | Modality | Total Duration | Target Audience | Course Goal | High‑level Objectives

### 6.2  Layer 1 — Content‑Map Table (see Appendix for column definitions)

*A4 landscape, sans‑serif ≥ 11 pt, adequate margins, footer with timestamp & page numbers, module ref*

| Module | Duration | Key Topics | Learning Objectives | Activities / Assessments (summary only) | Learning Outcomes | Instructional Alignment* |
| ------ | -------- | ---------- | ------------------- | --------------------------------------- | ----------------- | ------------------------ |
| …      | …        | …          | …                   | …                                       | …                 | Bloom / Gagné / Kirkpatrick / ARCS |

*All entries **must** trace directly to the locked Learning Outcomes and be theory‑aligned.*

### 6.3  Layer 2 — Appendix

For each activity/assessment from Layer 1, provide:

- **Detailed Activity Output** (full *Learning_Activity_Generator_Module* response)  
- **Differentiation & Scaffolding** details  
- **Accessibility** specifications  
- **Misconception Checks** (include threshold concepts & high‑priority misconceptions for SME review)  
- **Optional**: theory checklists, cognitive keyword watchlist highlights  

*Do **not** remix module outputs unless explicitly SME‑approved.*

---

## 7  Export Standards

- Deliver a single `.docx` containing **Layer 1** followed by **Layer 2**.  
- Document properties: A4 landscape, sans‑serif font ≥ 11 pt, consistent heading styles, automatic table of contents.  
- Footer on every page: generation timestamp · page X of Y · module reference code.

---

## 8  Error Handling & Optimisation

- **Error Report** — if validation fails at any stage, output a single bullet list summarising all missing data or mismatches; do not proceed further.  
- **Optimise runtime** by modularising validation checks, supporting the `module_id` partial‑rerun parameter and setting global export settings.

---

*End of prompt.*
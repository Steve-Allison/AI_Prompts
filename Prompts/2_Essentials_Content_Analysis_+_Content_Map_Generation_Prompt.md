# Unified_Content‑Map_Generation_&_Analysis_Prompt

_(version - 3 – incorporates regex fallbacks, resilient JSON extraction, and per‑module default export)_

---

## ⚠️ Execution Directive

All instructions in this prompt are **mandatory**. Do **not** skip, approximate or substitute any step.  
If a requirement is unmet, **halt immediately** and output a single bullet‑list error report.  
Placeholder or partial outputs are **forbidden**.

---

## 0 Source Materials (OneDrive, read‑only)

`https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g`

| Purpose                                | **Exact / Pattern‑Matched File Name**                                         |
| -------------------------------------- | ----------------------------------------------------------------------------- |
| Course structure (8‑module outline)    | **Essentials_course_structure.md**                                            |
| Learning gap, goal & objectives        | **\*\_Essentials_Learning_Design.md** (any prefix)                            |
| Prompt‑module definitions              | **ai_prompt_modules_minimal.md**                                              |
| Authoring instructions for content map | **\*\_Content_Map_Instructions_v3.md**                                          |
| Target‑audience personas               | **Adobe_Sellers_Learner_Personas.md** and/or **Adobe_SC_Learner_Personas.md** |

If any file above is missing or unreadable, invoke **Halt & Report**.

---

## 1 Global Instructions

| Requirement     | Details                                                       |
| --------------- | ------------------------------------------------------------- |
| **Language**    | British English only.                                         |
| **Memory**      | Clear all prior cache/memory before execution.                |
| **Tone**        | Clear, concise, instructional; matched to the target persona. |
| **Bloom Focus** | _Remember_ level (unless otherwise specified in objectives).  |
| **Assessment**  | End‑of‑course quiz plus module‑level checks (auto‑generated). |

---

## 2 Pre‑Flight Validation

1. Confirm all files in **Section 0** are attached.
   - Four must match **exactly**.
   - One must satisfy the pattern `*_Essentials_Learning_Design.md`.
2. If any file is missing/unreadable, output a bullet‑list of those items and **stop processing**.

---

## 3 Core Data to Extract & Lock

| Data                                   | Extraction rule                                                                                                                     |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------ | --------------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Learning Gap, Goal & Objectives**    | Copy verbatim from _\_Essentials_Learning_Design.md_.                                                                               |
| **8‑Module Course Structure**          | Extract from _Essentials_course_structure.md_.                                                                                      |
| **Delivery Mode → `mode`**             | Parse the first heading/table cell matching \*\*`/Modality                                                                          | Delivery[ _-]?Mode | Delivery[ _-]?Type/i`**; if no match, default to `"self‑paced e‑learning"`. |
| **Assessment Plan → `assessment`**     | Parse the first heading/cell matching \*\*`/Assessment                                                                              | Evaluation         | Quiz                                                                        | Test/i`**; if no match, default to `"end‑of‑course quiz"`. |
| **Target Persona → `learner_profile`** | Locate the **first fenced block tagged `json learner_profile`; if absent, use the first JSON block found** in the persona MD files. |

All five locked items are immutable downstream.

---

## 4 AI Prompt Modules (available)

| Module                                            | Primary role                                                                                                               |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Learner_Outcomes_Module**                       | Expand & validate gaps → goals → objectives → outcomes                                                                     |
| **Learning_Activity_Generator_Module**            | Create formative activities **and** summative assessments (requires `objectives`, `assessment`, `mode`, `learner_profile`) |
| **Learning_Asset_Module**                         | Recommend asset types & formats                                                                                            |
| **Pedagogy_Module**                               | QA objectives & scaffold sequencing                                                                                        |
| **Differentiation_Scaffolding_Module**            | Differentiation tiers & supports                                                                                           |
| **Misconception_Check_Module**                    | Threshold concepts & misconceptions                                                                                        |
| **Accessibility_Module**                          | WCAG 2.2 AA compliance                                                                                                     |
| **Tone_of_Voice_Module**                          | Persona‑appropriate voice                                                                                                  |
| **Visual_Style_Module**                           | Clean, accessible, corporate look                                                                                          |
| _Optional_ **Learning_Theories_Checklist_Module** | Bloom, Gagné, SOLO alignment                                                                                               |
| _Optional_ **Cognitive_Keyword_Watchlist_Module** | Cognitive/emotional load flags                                                                                             |

---

## 5 Execution Sequence

| #     | Action                                     |
| ----- | ------------------------------------------ |
| **1** | **Run Pre‑Flight Validation** (Section 2). |
| **2** | **Extract variables**: \                   |

• `mode`, `assessment` via regex rules (Section 3) \  
  • `learner_profile` via JSON extraction rule. |
| **3** | **Generate & validate** gaps, goals, objectives & outcomes (_Learner_Outcomes_Module_). |
| **4** | **Map** validated content to the eight modules. |
| **5** | **Align** items to instructional‑theory tags (Bloom, Gagné, Kirkpatrick, ARCS). |
| **6** | **Accessibility pre‑check** – run _Accessibility_Module_; halt if WCAG fails. |
| **7** | **Generate activities & assessments** via _Learning_Activity_Generator_Module_, passing: `objectives, assessment, mode, learner_profile`. Then run: <br>• _Differentiation_Scaffolding_Module_ <br>• _Misconception_Check_Module_ <br>_(Tip: include `module_id` to produce or regenerate **one module at a time** for SME review and to conserve context.)_ |
| **8** | **Accessibility final‑check** – rerun _Accessibility_Module_ on the complete draft; halt if WCAG fails. |
| **9** | **Compliance Verification** – ensure structure, theory alignment, accessibility, tone & formatting are complete; halt if any element is missing. |
| **10** | **Assemble/export** `.docx` per Section 7. **Default**: export **one module at a time** in sequence. Use `module_id="all"` to output the full document in a single run. |

---

## 6 Output Specification

### 6.1 Document Header (populated from input documents)

**Course Title:** [populated from learning design input]  
**Generation Date:** [auto-generated timestamp]  
**Modality:** [populated from delivery mode extraction]  
**Duration:** [populated from course structure input]  
**Target Audience:** [populated from learner persona input]  
**Course Goal:** [populated from learning design input]  
**High-level Objectives:** [populated from learning design input]

### 6.2 Layer 1 — Content‑Map Table

**Mandatory Formatting Requirements:**
- **Page Size:** A4
- **Orientation:** Landscape  
- **Margins:** 1cm all around
- **Font:** Sans-serif, 11pt
- **Header:** Content Map title
- **Footer:** Timestamp and module reference

| Column                       | Definition                              |
| ---------------------------- | --------------------------------------- |
| **Module**                   | Numerical/descriptive label             |
| **Duration**                 | Seat‑time or effort                     |
| **Key Topics**               | Primary subject areas                   |
| **Learning Objectives**      | Behavioural objectives                  |
| **Activities / Assessments** | One‑line descriptors                    |
| **Learning Outcomes**        | Verbatim outcomes                       |
| **Instructional Alignment**  | Bloom / Gagné / Kirkpatrick / ARCS tags |

### 6.3 Layer 2 — Appendix

For each activity/assessment in Layer 1 provide:

- Detailed activity output (_Learning_Activity_Generator_Module_)
- Differentiation & scaffolding details
- Accessibility specifications
- Misconception checks
- _Optional_: learning‑theory checklist & cognitive keyword flags

_No remixing of module outputs unless SME‑approved._

---

## 7 Export Standards

- Single `.docx` containing Layer 1 followed by Layer 2 (or per‑module `.docx` when using `module_id`).
- A4 landscape, sans‑serif ≥ 11 pt, consistent heading styles, auto TOC.
- Footer every page: generation timestamp · page X of Y · module reference code.

---

## 8 Error Handling & Optimisation

- **Error Report** – any validation/compliance failure → one bullet‑list; processing stops.
- **Optimise runtime** – modular validation, supports `module_id` partial rerun.
- **No placeholders** – if required data are missing, halt & report rather than outputting incomplete content.

---

_End of prompt._

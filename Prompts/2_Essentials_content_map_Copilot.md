# Unified Content‑Map Generation & Analysis Prompt  
_(version 3.1 – adds Supported‑File rules, Learning‑Goal/Objective alignment, Course‑Structure authority, and explicit folder‑scan directive)_

---

## ⚠️ Execution Directive  
All instructions in this prompt are **mandatory**. Do **not** skip, approximate or substitute any step.  
If a requirement is unmet, **halt immediately** and output a single bullet‑list error report.  
Placeholder or partial outputs are **forbidden**.

---

## 0 Source Materials (OneDrive, read‑only)  

You MUST iterate through **every file contained in `SOURCE_FOLDER`** (including sub‑folders), extract all machine‑readable text, and store that text for downstream analysis. No content may be discarded unless it is an exact duplicate of another file.

All files in the linked folder must be read and analysed for relevant content, unless a specific file requirement or exclusion is stated below. Use all available information from these files to inform the outputs of this prompt:

`https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g`

| Purpose | **Required File Name or Pattern** | Notes |
|---------|-----------------------------------|-------|
| Prompt‑module definitions | `Adobe_FRE_mini_omni_Supporter.md` | Must contain all module definitions and metadata. |
| Learning gap, goal & objectives | `Marketo_Essentials_Learning_Design.md` | Must be a **separate file** containing actual course‑specific content. **Do not accept instructional templates or guidance‑only files.** |

> ⚠️ **Important Validation Rule:**  Files must be **stand‑alone** unless explicitly defined as modular containers. Do **not** accept instructional templates or guidance‑only sections as substitutes for required course‑specific files.

### 0.1 Supported File‑Types & Extraction Rules  

| Extension | Typical source | Extraction method | Notes |
|-----------|----------------|-------------------|-------|
| `.docx` | Word | Parse body, headings, tables, comments, alt‑text (include Track‑Changes). |
| `.xlsx` | Excel | Convert every sheet to CSV; treat each row as a paragraph (include hidden sheets). |
| `.pptx` | PowerPoint | Extract slide titles, on‑slide text, speaker notes, alt‑text (skip masters). |
| `.pdf` | PDF | Attempt direct extraction; if no text layer, run OCR; else list in error report. |
| `.vtt` | WebVTT | Merge caption blocks into single transcript per file. |
| _Other_ | — | Best‑effort scrape; if unsupported, list in error report. |

---

## 1 Global Instructions  

| Requirement | Details |
|-------------|---------|
| **Language** | British English only. |
| **Memory** | Clear all prior cache/memory before execution. |
| **Tone** | Clear, concise, instructional; matched to the target persona. |
| **Bloom Focus** | _Remember_ level (unless otherwise specified). |
| **Assessment** | End‑of‑course quiz plus module‑level checks (auto‑generated). |

---

## 2 Pre‑Flight Validation  

1. Confirm all files in Section 0 are attached (one exact, one matching `*_Essentials_Learning_Design.md`).  
2. Run extraction routines in Section 0.1.  
3. If any file is missing/unreadable, bullet‑list and pause; else proceed to Section 3.

---

## 3 Core Data to Extract & Lock  

| Data | Extraction rule |
|------|-----------------|
| **Learning Gap, Goal & Objectives** | Verbatim from `_Essentials_Learning_Design.md`. |
| **8‑Module Course Structure** | Extract from `Essentials_course_structure`. |
| **Delivery Mode → `mode`** | First heading/table cell matching `/Modality|Delivery[ _-]?Mode|Delivery[ _-]?Type/i`; default `"self‑paced e‑learning"`. |
| **Assessment Plan → `assessment`** | First heading/cell matching `/Assessment|Evaluation|Quiz|Test/i`; default `"end‑of‑course quiz"`. |
| **Target Persona → `learner_profile`** | First fenced block tagged `json learner_profile(s)` in persona files; else first valid JSON block. |

When extracting **Duration**, match any field labelled *Duration* or *Suggested Timings* (case‑insensitive).  
All five locked items are immutable downstream.

---

## 4 AI Prompt Modules (available)  

Learner_Outcomes_Module · Learning_Activity_Generator_Module · Learning_Asset_Module · Pedagogy_Module · Differentiation_Scaffolding_Module · Misconception_Check_Module · Accessibility_Module · Tone_of_Voice_Module · Visual_Style_Module  
_Optional:_ Learning_Theories_Checklist_Module · Cognitive_Keyword_Watchlist_Module

---

## 5 Execution Sequence  

1. **Run Pre‑Flight Validation**.  
2. **Extract variables** (Section 3).  
3. **Generate & validate** gaps, goals, objectives & outcomes (Learner_Outcomes_Module).  
4. **Map** validated content to the eight modules.  

   **4 a. Learning‑Goal & Objective Alignment Rule** – Every Key Topic/Sub‑topic must align explicitly with the locked Goal and Objectives (verbatim). If no alignment, omit or error‑list. Add Objective ID in brackets after each Learning Objective.

   **4 b. Course‑Structure Authority Rule** – The eight modules in `Essentials_course_structure` are authoritative. Use module titles verbatim; derive all topics/sub‑topics only from their respective blocks. Halt if module count ≠ 8 or required topic missing.

5. **Align** items to Bloom, Gagné, Kirkpatrick, ARCS tags.  
6. **Accessibility pre‑check** (Accessibility_Module) – halt if WCAG fails.  
7. **Generate activities & assessments** (Learning_Activity_Generator_Module) → Differentiation_Scaffolding_Module → Misconception_Check_Module.  
8. **Accessibility final‑check**.  
9. **Compliance verification** – halt if any element missing.  
10. **Assemble/export** `.docx` per Section 7 (per‑module or full).  

---

## 6 Output Specification  

### 6.1 Document Header  
Course Title · Generation Date · Modality · Duration · Target Audience · Course Goal · High‑level Objectives

### 6.2 Layer 1 – Content‑Map Table  

Module · Duration · Key Topics · Sub‑topics · Learning Objectives (with ID) · Activities/Assessments · Learning Outcomes · Instructional Alignment

### 6.3 Layer 2 – Appendix  

For each activity/assessment: detailed output · differentiation · accessibility · misconception checks · (optional) theory checklist & cognitive flags.

---

## 7 Export Standards  

Landscape A4 DOCX · 1 cm margins · sans‑serif 11 pt · header “Content Map” · footer timestamp & module reference.  
End every output section with the audit‑trail line.  
Generate a downloadable link; **do not inline WordML/XML**.

---

## 8 Error Handling & Optimisation  

Bullet‑list error report on any failure; proceed where possible. Modular validation supports `module_id` reruns. No placeholders. SME override logs allowed.

---

## 9 Glossary  

Locked · Halt · SME · module_id

---

_End of prompt._

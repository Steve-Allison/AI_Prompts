# Unified_Content‑Map_Generation_and_Analysis_Prompt  

## (version_3.4 – adds JSON_handshake, enumerated_error_codes, RANDOM_SEED, strict_output_schemas, token‑budgets, chunk‑size_ceiling, and MIME_fallback)

---

## ⚠️_Execution_Directive  

All numbered instructions are **mandatory**. If any requirement is unmet, **halt immediately** and output a single bullet‑list error report using the **enumerated error codes** in §10.  
No placeholder text is permitted; every section must be complete.

---

## 0 Source Materials (OneDrive, read‑only)  

You **must** iterate through **every file contained in `SOURCE_FOLDER`** (including sub‑folders), extract all machine‑readable text, and store that text for downstream analysis.  

`SOURCE_FOLDER` → <https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g>  

No content may be discarded unless it is an exact duplicate of another file.  

| Purpose | **Required file name or pattern** | Notes |
|---------|-----------------------------------|-------|
| Prompt‑module definitions | `Adobe_FRE_mini_omni_Supporter.md` | Contains reusable AI modules **and** `Essentials_course_structure`. |
| Learning gap, goal & objectives | `*_Essentials_Learning_Design.md` | Must be stand‑alone, course‑specific (not a template). |

> **Validation:** If either file is missing or unreadable, emit **E01** and halt.

---

###  0.1 Supported File‑Types & Extraction Rules

| Extension | Typical source | Extraction method |
|-----------|----------------|-------------------|
| `.docx`   | Word | Extract body, Heading 1‑3, tables, comments, alt‑text (include Track‑Changes). **Chunk any document into ≤ 15 000 characters per chunk before vectorising.** |
| `.pptx`   | PowerPoint | Extract slide **titles only**; ignore body bullets and speaker notes for topic mining, but keep full body text for relevance scoring. |
| `.xlsx`   | Excel | Convert every sheet to CSV; treat row 1 headers and sheet names as headings. |
| `.pdf`    | PDF | Extract bookmarks/outlines; if absent, detect lines ≥ 1.3× body font size. OCR fallback if no text layer. |
| `.vtt`    | WebVTT | Merge caption blocks (body text only; captions are not headings). |
| _Other_   | — | Attempt plain‑text extraction; if unsupported, emit **E02**. |

---

##  1 Global Instructions  

| Requirement | Details |
|-------------|---------|
| **Language** | British English only |
| **Memory** | Clear all prior cache/memory before execution |
| **Tone** | Clear, concise, instructional |
| **Bloom focus** | _Remember_ level unless otherwise authorised |
| **Assessment** | End‑of‑course quiz plus module‑level checks (auto‑generated) |
| **Randomness** | If `RANDOM_SEED` env variable is provided, initialise the model’s random state; otherwise run with temperature 0 |

---

##  2 Pre‑Flight Validation  

1. Confirm that both required files in **§0** are present and readable.  
2. Run extraction routines in **§0.1** on _all_ files in `SOURCE_FOLDER`.  
3. If any file fails extraction (E01 / E02), halt.

###  2.5 JSON Handshake (mandatory)  

Immediately output a JSON object exactly matching the schema below. Generation may continue **only if** `"ready_to_proceed": true`.

```json
{
  "handshake": {
    "timestamp": "2025-06-06T12:00:00Z",
    "core_files_found": true,
    "modules_detected": 8,
    "hashes_locked": false,
    "ready_to_proceed": false
  }
}
```

Populate the keys, then lock core hashes in §3 and update `"hashes_locked"` and `"ready_to_proceed"` accordingly.  
If any flag is `false`, emit the relevant error codes and halt.

---

##  3 Core Data to Extract & Lock  

| Data | Extraction rule (immutable after this step) |
|------|---------------------------------------------|
| Learning Gap | Line directly under a heading that contains the phrase “Learning Gap” (case‑insensitive, any heading level, punctuation ignored) |
| Learning Goal | Line directly under a heading that contains the phrase “Learning Goal” |
| Learning Objectives | Bullet list under a heading that contains the phrase “Learning Objectives” (or “Objectives”) |
| 8‑Module Course Structure | Exact from `Essentials_course_structure` table |
| Delivery Mode → `mode` | First heading or cell containing any of the keywords **Modality**, **Delivery Mode**, or **Modality/Content Type** (case‑insensitive) |
| Assessment Plan → `assessment` | First heading or cell containing **Assessment**, **Assessment Plan**, or **Assessment Strategy** (case‑insensitive) |
| Target Persona → `learner_profile` | Extract from `__Learner_Personas.md` if present |
| Duration | Prefer “Suggested Timings” (course‑structure) over any “Duration” field |

Store each item’s SHA‑256 hash; set `"hashes_locked": true` in the handshake.

---

##  4 Heading‑Level Topic Mining & Module Mapping  

> **Objective:** Produce a vetted list of _Key Topics_ and _Sub‑topics_ derived **only** from heading‑level artefacts, with relevance scored using the full document corpus.

###  4.1 Candidate Heading Harvest  

| File‑type | Accepted heading sources |
|-----------|--------------------------|
| `.pptx`   | Slide titles |
| `.docx`   | Paragraphs styled Heading 1‑3 |
| `.pdf`    | Bookmarks/outlines; otherwise lines ≥ 1.3× body font size |
| `.xlsx`   | Sheet names + row 1 header cells |
| Others    | Headings detected by style/size heuristics |

Record **file‑path → section → heading hierarchy** for each heading.

###  4.2 Relevance Scoring  

1. Embed each heading and each locked Learning Objective.  
2. Compute cosine similarity.  
3. Increase weight if surrounding body text shares key terms.  
4. Discard headings with weighted score < 0.75.

###  4.3 Topic ↔ Sub‑topic Inference  

* Use heading nesting to establish hierarchy.  
* Deepest heading = **Sub‑topic**; parent heading = **Topic**.  
* Single-level paths become stand‑alone Topics.

###  4.4 Essentials Module Assignment  

* Locate the Markdown table whose first header row (case‑insensitive) contains **module title** and **suggested timings** (accepts header aliases such as _title_ or _timings_).—this is treated as the **Essentials_course_structure** table (case‑insensitive search). Treat the first row as headers and extract the **“Module Title”** column for authoritative module names. Halt **E13** if the table or headers are not detected.  
* For each (Topic, Sub‑topic) pair, compute similarity to the eight module titles.  
* Assign to the highest‑scoring module (≥ 0.75).  
* If no module ≥ 0.75, send to SME Review list and halt.

###  4.5 Audit Trail — Topic Alignment Report  

```markdown
| Topic | Sub‑topic | Source File | Path | Assigned Module | Objective ID | Score |
|-------|-----------|-------------|------|-----------------|--------------|-------|
| Reporting | Metrics vs KPIs | reporting_deck.pptx | Slide 5 | Module 1 | OBJ‑2 | 0.87 |
```

_Coverage check_ — halt **E03** if < 90 % of objective verbs appear.  
_Duplicate check_ — halt **E04** if duplicate topics across modules.

---

##  5 Leveraged AI Prompt Modules  

| Workflow Stage | Module | Purpose |
|----------------|--------|---------|
| Topic & Outcomes | `Learner_Outcomes_Module` | Validates gaps and outputs SMART objectives |
| Activity Creation | `Learning_Activity_Generator_Module` | Builds scaffolded activities |
| Alignment QA | `Pedagogy_Module` | Tags Bloom, Gagné, ARCS |
| Accessibility | `Accessibility_Module` | WCAG 2.2 AA compliance |
| Enrichment | `Misconception_Check_Module` | Adds misconception handling |

---

##  6 Execution Sequence  

1. Pre‑Flight Validation — §2  
2. JSON Handshake — §2.5  
3. Extract & Lock Core Data — §3  
4. Heading‑Level Topic Mining & Mapping — §4  
5. Generate Layer 1 Content Map  
   * Insert Topics/Sub‑topics into correct module rows.  
   * Call `Learner_Outcomes_Module` → Learning Outcomes column.  
   * Call `Learning_Activity_Generator_Module` → Activities/Assessments column.  
6. Tag each row with Bloom, Gagné, Kirkpatrick & ARCS via `Pedagogy_Module`.  
7. Accessibility Pre‑Check via `Accessibility_Module`.  
8. Differentiation & Misconception enrichment.  
9. Accessibility Final‑Check.  
10. Compliance verification (hashes, duplicates, token budgets).  
11. Assemble & export DOCX.

---

##  7 Output Specification  

###  7.1 Document Setup  

| Field | Sample Value |
|-------|--------------|
| Course Title | “Marketo Essentials” |
| Generation Date | 2025‑06‑06 |
| Modality | Blended (VILT + Self‑paced) |
| Duration | 180 minutes |
| Target Audience | New Marketo Administrators |
| Learning Goal | Improve daily marketing‑automation tasks |
| High‑level Objectives | OBJ‑1 Identify key metrics; OBJ‑2 Build basic nurture |

###  7.2 Layer 1 — Content‑Map Table  

```markdown
| Module ID | Module Title | Duration | Key Topics | Sub‑topics | Learning Objectives (ID) | Activities / Assessments | Learning Outcomes |
| 1 | Reporting & Analytics | 45 min | Reporting | Metrics vs KPIs | OBJ‑2 | Quiz + demo | Learners can identify key metrics |
```

###  7.3 Layer 2 — Appendix Schema  

```markdown
| Module ID | Module Title | Key Topic | Sub‑topic | Activity / Assessment Output | Differentiation & Scaffolding | Accessibility (WCAG 2.2 AA) | Instructional Alignment (Bloom / Gagné / Kirkpatrick / ARCS) | Misconception Checks | Optional: Theory / Cognitive Flags |
```

###  7.4 Topic Alignment Report  

Include the audit table from §4.5 after the appendix.

---

##  8 Export Standards  

Landscape A4 DOCX — 595.28 pt × 841.89 pt; 1 cm margins; sans‑serif 11 pt; header “Content Map”; footer timestamp + module reference.  
Provide a download link (no inline WordML/XML).  
End every section with an audit‑trail line: “Generated: 2025‑06‑06 12:00 UTC”.

---

##  9 Token‑Budget Targets  

* ≤ 4 000 tokens for Layer 1 table.  
* ≤ 6 000 tokens for appendix + audit trail.

---

##  10 Enumerated Error Codes  

| Code | Meaning |
|------|---------|
| **E01** | Core file missing/unreadable |
| **E02** | Unsupported file type extraction failed |
| **E03** | Objective coverage < 90 % |
| **E04** | Duplicate topics across modules |
| **E05** | Token budget exceeded |
| **E06** | Schema mismatch, missing heading, or empty locked value |
| **E07** | Accessibility failure |
| **E08** | Hash mismatch |
| **E09** | Unknown error |
| **E10** | Reserved / future use |
| **E13** | Module table parse fail |

---

_End of prompt._

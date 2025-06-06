# Unified_Content_Map_Generation & Analysis_Prompt

## (version 3.4 – adds JSON_handshake, enumerated_error codes, RANDOM_SEED, strict_output_schemas, token_budgets, chunk_size_ceiling, and MIME fallback)

---

## ⚠️*Execution* Directive

All numbered instructions are **mandatory**. If any requirement is unmet, **halt immediately** and output a single bullet‑list error report using the **enumerated error codes** in §10.  
Placeholder or partial outputs are **forbidden**.

---

## 0 Source Materials (OneDrive, read‑only)

You **must** iterate through **every file contained in `SOURCE_FOLDER`** (including sub‑folders), extract all machine‑readable text, and store that text for downstream analysis.

`SOURCE_FOLDER` → <https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g>

No content may be discarded unless it is an exact duplicate of another file.

| Purpose                         | **Required file name or pattern**  | Notes                                                               |
| ------------------------------- | ---------------------------------- | ------------------------------------------------------------------- |
| Prompt‑module definitions       | `Adobe_FRE_mini_omni_Supporter.md` | Contains reusable AI modules **and** `Essentials_course_structure`. |
| Learning gap, goal & objectives | `*_Essentials_Learning_Design.md`  | Must be stand‑alone, course‑specific (not a template).              |

> **Validation:** If either file is missing/unreadable, emit **E01** and halt.

---

###  0.1 Supported File‑Types & Extraction Rules

| Extension | Typical source | Extraction method                                                                                                                                            |
| --------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `.docx`   | Word           | Extract body, Heading 1‑3, tables, comments, alt‑text (include Track‑Changes). **Chunk any document into ≤ 15 000 characters per chunk before vectorising.** |
| `.pptx`   | PowerPoint     | Extract slide **titles only** (ignore body bullets and speaker notes for topic mining, but keep body text for relevance scoring).                            |
| `.xlsx`   | Excel          | Convert every sheet to CSV; treat row 1 headers and sheet names as headings.                                                                                 |
| `.pdf`    | PDF            | Extract bookmarks/outlines; if absent, detect lines ≥ 1.3× body font size. OCR fallback if no text layer.                                                    |
| `.vtt`    | WebVTT         | Merge caption blocks (body text only, never headings).                                                                                                       |
| *Other*   | —              | **MIME fallback:** attempt plain‑text extraction; if still unreadable, emit **E02**.                                                                         |

---

##  1 Global Instructions

| Requirement     | Details                                                                                                                                                                 |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Language**    | British English only.                                                                                                                                                   |
| **Memory**      | Clear all prior cache/memory before execution.                                                                                                                          |
| **Tone**        | Clear, concise, instructional; matched to the target persona.                                                                                                           |
| **Bloom focus** | *Remember* level unless otherwise authorised.                                                                                                                           |
| **Assessment**  | End‑of‑course quiz plus module‑level checks (auto‑generated).                                                                                                           |
| **Randomness**  | If environment variable `RANDOM_SEED` is supplied, initialise the model’s random state to that value (if supported). Otherwise run determinstically with temperature 0. |

---

##  2 Pre‑Flight Validation

1. Confirm required files in **§0** are present & readable.
2. Run extraction routines in **§0.1** on *all* files in `SOURCE_FOLDER`.
3. If any file fails extraction (E01 / E02), halt.

###  2.5 JSON Handshake (mandatory)

Immediately output a JSON object exactly matching the schema below. Generation may continue **only if** `"ready_to_proceed": true`.

```json
{
  "handshake": {
    "timestamp": "<ISO‑8601>",
    "core_files_found": true,
    "modules_detected": 8,
    "hashes_locked": false,
    "ready_to_proceed": false
  }
}
```

Populate the keys, then lock core hashes in §3 and update `"hashes_locked"`, `"ready_to_proceed"` accordingly.  
If any flag is `false`, emit the relevant error codes and halt.

---

##  3 Core Data to Extract & Lock

| Data                               | Extraction rule (immutable)                                              |
| ---------------------------------- | ------------------------------------------------------------------------ |
| Learning Gap, Goal & Objectives    | Verbatim from `*_Essentials_Learning_Design.md`                          |
| 8‑Module Course Structure          | Exact from `Essentials_course_structure` table.                          |
| Delivery Mode → `mode`             | First heading/cell `/Modality/i`.                                        |
| Assessment Plan → `assessment`     | First heading/cell `/Assessment/i`.                                      |
| Target Persona → `learner_profile` | From `__Learner_Personas.md` if present.                                 |
| Duration                           | Prefer “Suggested Timings” (course structure) over any “Duration” field. |

Store each item’s SHA‑256 hash; set `"hashes_locked": true` in the handshake.

---

##  4 Heading‑Level Topic Mining & Module Mapping

*Unchanged from v3.3 except for chunk ceiling already defined.*

(Candidate harvest §4.1, relevance scoring §4.2, inference §4.3, module assignment §4.4, audit trail §4.5 remain identical.)

---

##  5 Leveraged AI Prompt Modules

(Same table as v3.3.)

---

##  6 Execution Sequence

1. Pre‑Flight Validation – §2
2. JSON Handshake – §2.5
3. Extract & Lock Core Data – §3
4. Heading‑Level Topic Mining & Module Mapping – §4
5. Generate Layer 1 Content Map (calls modules)
6. Pedagogical Alignment (`Pedagogy_Module`)
7. Accessibility Pre‑Check (`Accessibility_Module`)
8. Differentiation & Scaffolding (`Differentiation_Scaffolding_Module`)
9. Misconception Check (`Misconception_Check_Module`)
10. Accessibility Final‑Check (`Accessibility_Module`)
11. Compliance Verification & hash re‑check
12. Assembly & Export

*Layer 1 + appendix must respect token budgets: **≤ 4 000 tokens** for Layer 1, **≤ 6 000 tokens** for appendix + audit trail. Exceeding emits **E06**.*

---

##  7 Output Schemas

###  7.1 Layer 1 Content‑Map (strict Markdown)

```markdown
| Module ID | Module Title | Duration | Key Topics | Sub‑topics | Learning Objectives (ID) | Activities / Assessments | Learning Outcomes |
| 1 | Example Module | 45 min | Reporting | Metrics vs KPIs | LO‑1 | Quiz + demo | Learners can identify… |
```

*No additional columns, no reordered headers.* Any deviation triggers **E07**.

###  7.2 Appendix & Topic Alignment Report

(Follow schemas from v3.3.)

---

##  8 Export Standards

(Same as v3.3.)

---

##  9 Token‑Budget Hints

- When generating Layer 1 rows, **aim ≤ 150 tokens per module**.
- For appendix rows, **aim ≤ 120 tokens per row**.
- If the model cannot meet budgets, summarise gracefully rather than truncate mid‑cell.

---

##  10 Enumerated Error Codes

| Code    | Meaning                                            |
| ------- | -------------------------------------------------- |
| **E01** | Required core file missing/unreadable              |
| **E02** | Unsupported file type – fallback extraction failed |
| **E03** | Coverage < 90 % of objective verbs                 |
| **E04** | Duplicate topic detected across modules            |
| **E05** | No module similarity ≥ 0.75 for a topic            |
| **E06** | Token budget exceeded for specified section        |
| **E07** | Output schema mismatch (Layer 1)                   |
| **E08** | Accessibility check failed                         |
| **E09** | SHA‑256 hash mismatch (tampered locked data)       |
| **E10** | Unknown / unclassified error                       |

On failure, output **only** a bullet‑list of `(code) – description`.

---

*End of prompt.*

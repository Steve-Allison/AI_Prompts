# Course‑Content_Generator_Prompt

## (version 3.6 – persona file mandatory; adds Cognitive Keyword Watchlist, adaptive similarity fallback, Visual Style stamping, topic‑specific depth hints)

---

## ⚠️ Execution Directive

All numbered instructions are **mandatory**. If any requirement is unmet, **halt immediately** and output a single bullet‑list of enumerated error codes in §12.  
No placeholders or partial outputs.

---

##  0 Required Inputs

| Purpose                     | File(s) / Handle(s)                                    | Notes                                                                                                |
| --------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| **Locked Content‑Map**      | `CONTENT_MAP.md` **or** `CONTENT_MAP.docx`             | Must conform to the Layer 1 & Layer 2 schema of the Content‑Map prompt v3.4.                         |
| **Learner Persona profile** | `__Learner_Personas.md` **or** `*_Learner_Personas.md` | Mandatory. Must describe at least one primary persona for differentiation.                           |
| **Source corpus**           | Entire `SOURCE_FOLDER` from the Content‑Map run        | URL: <https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g> |

> **E01** if the Content‑Map is missing/invalid.  
> **E14** if the Learner‑Persona file is missing or empty.

---

##  1 Global Settings

| Setting              | Value / Behaviour                                                          |
| -------------------- | -------------------------------------------------------------------------- | ----------------------- | ------------------------------------------------------------------------------------- |
| **Language**         | British English                                                            |
| **Memory**           | Flush all prior state before run                                           |
| **Randomness**       | Honour `RANDOM_SEED=<int>`; else temperature 0                             |
| **Token Budgets**    | ≤ 3 000 tokens **per module**; ≤ 24 000 tokens total                       |
| **Chunk Ceiling**    | Split any chunk > 15 000 chars                                             |
| **Accessibility**    | Must pass WCAG 2.2 AA                                                      |
| **Readability**      | UK Flesch Grade ≤ 10                                                       |
| **Citation Style**   | `CITATION_STYLE=harvard                                                    | ieee` (default harvard) |
| **Depth**            | `DEPTH=brief                                                               | standard                | deep` (default standard) <br>Override per‑topic via YAML front‑matter in Content Map: |
| **Asset Generation** | `ASSET_GEN=true` ⇒ `image_gen` call & Visual_Style stamping “Version 2025” |
| **Selective Rerun**  | `module_id=[array]` regenerates only listed modules                        |

---

##  2 ENV Variable Quick Reference

```bash
RANDOM_SEED=<int>
DEPTH=brief|standard|deep
CITATION_STYLE=harvard|ieee
ASSET_GEN=true|false
EXPECTED_MODULES=<int>      # override default 8
KEYWORD_WATCHLIST=term1,term2,…   # optional; else default Marketo list
module_id=[1,4,6]
```

Default `KEYWORD_WATCHLIST`: _lead scoring, smart list, engagement stream, nurture, Salesforce sync, program status_.

---

##  3 Enumerated Error Codes

| Code    | Meaning                              |
| ------- | ------------------------------------ |
| **E01** | Content‑Map missing / invalid        |
| **E02** | Source file unreadable / unsupported |
| **E03** | JSON handshake flags false           |
| **E04** | WCAG 2.2 failure                     |
| **E05** | Token budget exceeded                |
| **E06** | Output schema mismatch               |
| **E07** | Required module package missing      |
| **E08** | SHA‑256 hash mismatch                |
| **E09** | Duplicate concept across modules     |
| **E10** | Reserved / future                    |
| **E11** | Readability grade > 10               |
| **E12** | Missing citation in Source‑Trace     |
| **E13** | Module table parse fail              |
| **E14** | Learner‑Persona file missing/empty   |

---

##  4 Pre‑Flight Sequence

1. Validate Content‑Map (**E01**) and Persona file (**E14**).
2. Validate source corpus; fallback extraction (**E02**).
3. Confirm module count matches `EXPECTED_MODULES` (default 8).
4. Lock SHA‑256 hashes for map + persona + metadata.
5. **JSON Handshake**:

```json
{
  "handshake": {
    "timestamp": "2025-06-06T12:00:00Z",
    "content_map_found": true,
    "persona_found": true,
    "module_count": EXPECTED_MODULES_or_8,
    "hashes_locked": true,
    "ready_to_proceed": true
  }
}
```

Any `false` flag → **E03** halt.

---

##  5 Per‑Module Processing Loop

###  5.1 Data Mining

1. Embed all source chunks; cap 15 000 chars.
2. **Similarity scoring**: cosine to Topic/Sub‑topic **plus** keyword boost (2× weight) if chunk contains any term from `KEYWORD_WATCHLIST`.
3. **Adaptive threshold**: keep chunks ≥ 0.75; if < 3 chunks remain, rerun with threshold 0.65 or direct keyword search.

###  5.2 Layer Pipeline

| Layer                          | Module                                                              | Outputs                                                                                                               |
| ------------------------------ | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **L1 Foundation**              | `Learner_Outcomes_Module`                                           | Refined objectives; misconception list                                                                                |
| **L2 Content Dev.**            | `Learning_Activity_Generator_Module` + `Misconception_Check_Module` | Explanations, examples, visual brief                                                                                  |
| **L3 Scaffolding & Alignment** | `Differentiation_Scaffolding_Module` + `Pedagogy_Module`            | Support & stretch variants; Bloom/Gagné/ARCS tags (uses Persona data)                                                 |
| **L4 QA**                      | `Accessibility_Module`                                              | WCAG fixes; **Visual_Style_Module** adds “Version 2025” tag to any asset brief (plus `image_gen` if `ASSET_GEN=true`) |

###  5.3 Module Package Output (strict Markdown)

```markdown
### Module <ID> — <Module Title> (<Duration>)

**Topic ➞ Sub-topic:** <from Content-Map>

| Section                             | Content                              |
| ----------------------------------- | ------------------------------------ |
| Objectives (refined)                | (text)                               |
| Concept Explanation                 | (text)                               |
| Real-world Example                  | (text)                               |
| Visual Asset                        | Brief: (…) URL: (…)                  |
| Activity 1 (Core)                   | (text)                               |
| Activity 2 (Extension)              | (text)                               |
| Misconception Check                 | (text)                               |
| Differentiation (Support / Stretch) | (text)                               |
| Timing Table (min)                  | Intro • Explain • Activity • Debrief |
| Reflection Prompt                   | (text)                               |
| Extra Resources                     | (text)                               |
| Instructor Notes                    | (text)                               |
```

Token cap: 3 000 per module → **E05** if exceeded.

###  5.4 Source‑Trace Appendix

| Concept Section | File | Page/Slide | Hash‑snippet | Citation |

One row per explanation & example; missing citation → **E12**.

###  5.5 Readability Gate

Run `Readability_Module`; **E11** if Grade > 10.

---

##  6 Post‑Loop Aggregation

1. Agenda table.

**SME Tip** – Adjust the _Depth_ column in the Content‑Map for any topic and rerun only the affected module via `module_id=[n]`.  
2. Master Glossary (TF‑IDF top‑N across all modules).  
3. Re‑hash verify (**E08**).  
4. Duplicate scan (**E09**).  
5. Accessibility Final‑Check (**E04**).

---

##  7 Depth Handling

The writer first reads the **Depth** column from the Content‑Map’s Layer 1 table for each Topic row.
Priority order:

1. Depth value in Layer 1 row (_brief_, _standard_, _deep_).
2. Global `DEPTH` ENV variable.
3. If neither supplied, default = _standard_.

SMEs can change a Depth value in the map and rerun `module_id=[n]` to up‑ or down‑scope that topic.
If a YAML `depth_overrides` block also exists it is treated as a tie‑breaker only when the Depth column is blank.

---

##  8 Output & Export

Landscape A4 DOCX, “Course Pack”, header/footer, download link, audit‑trail line.

---

##  9 Rerun Procedure

`module_id=[…]` regenerates only listed modules; global gates still run.

---

##  10 Token‑Budget Targets

≤ 150 tokens per Topic table row; Support + Stretch text counts toward module budget.

---

##  11 Chunk‑Handling & Fallback Extraction

Same as Content‑Map prompt v 3.4.

---

##  12 Error‑Handling Summary

On failure, output bullet‑list of error codes + description. Codes > E10 are extensions; downstream should handle gracefully.

---

_End of prompt._

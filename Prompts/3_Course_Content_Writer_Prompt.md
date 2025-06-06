# Course-Content_Writer_Prompt

## (version 3.5 – fully aligned with “Unified Content-Map” v 3.4; adds Source-Trace Appendix, Readability gate, glossary, ENV controls, asset-generation hook and refined error handling)

---

## ⚠️ Execution Directive

All numbered instructions are **mandatory**. If any requirement is unmet, **halt immediately** and output a single bullet-list of the enumerated error codes in §11.  
No placeholders and no partial outputs are permitted.

---

## 0 Required Inputs

| Purpose                | File(s) / Handle(s)                                | Notes                                                                                                |
| ---------------------- | -------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Locked Content-Map** | `CONTENT_MAP.md` **or** `CONTENT_MAP.docx`         | Must conform to the Layer 1 & Layer 2 schema defined in the “Unified Content-Map” prompt v 3.4.      |
| **Source corpus**      | Entire `SOURCE_FOLDER` used in the previous prompt | URL: <https://adobe-my.sharepoint.com/:f:/p/sallison/EqVn3P8pbLZCsEiPMzojt_UBjdgSJ32e8W1TJ8nTRkQP8g> |

> **E01** if the Content-Map file is missing, unreadable, or fails schema validation.  
> When **E01** is emitted, also output: “Please attach a valid Content-Map file (Layer 1 & Layer 2) and rerun.”

---

## 1 Global Settings

| Setting              | Value / Behaviour                                                                        |
| -------------------- | ---------------------------------------------------------------------------------------- | --------------------------- | ---------------------------- |
| **Language**         | British English                                                                          |
| **Memory**           | Flush all prior state before run                                                         |
| **Randomness**       | Honour `RANDOM_SEED=<int>` if provided; otherwise run deterministically (temperature 0). |
| **Token Budgets**    | ≤ 3 000 tokens **per module package**; ≤ 24 000 tokens total.                            |
| **Chunk Ceiling**    | Break any source chunk > 15 000 characters before embedding or scoring.                  |
| **Accessibility**    | Must pass WCAG 2.2 AA.                                                                   |
| **Readability**      | Learner-facing text must score UK Flesch Grade ≤ 10.                                     |
| **Citation Style**   | Controlled by `CITATION_STYLE=harvard                                                    |  ieee` (default _harvard_). |
| **Depth**            | Controlled by `DEPTH=brief                                                               |  standard                   |  deep` (default _standard_). |
| **Asset Generation** | If `ASSET_GEN=true`, send each Visual Asset Brief to `image_gen`; store returned URL.    |
| **Selective Rerun**  | Caller may pass `module_id=[array]` to regenerate only specific modules.                 |

---

## 2 ENV Variable Quick Reference

```bash
RANDOM_SEED=<int>
DEPTH=brief|standard|deep
CITATION_STYLE=harvard|ieee
ASSET_GEN=true|false
module_id=[1,4,6]      # optional subset for rerun
```

---

## 3 Enumerated Error Codes

| Code    | Meaning                                             |
| ------- | --------------------------------------------------- |
| **E01** | Content-Map missing / invalid                       |
| **E02** | Source file unreadable / unsupported after fallback |
| **E03** | JSON handshake flags false                          |
| **E04** | WCAG 2.2 failure                                    |
| **E05** | Token budget exceeded                               |
| **E06** | Output schema mismatch                              |
| **E07** | Required module package missing                     |
| **E08** | SHA-256 hash mismatch                               |
| **E09** | Duplicate concept across modules                    |
| **E10** | Unknown / unclassified error                        |
| **E11** | Readability grade > 10                              |
| **E12** | Missing citation row in Source-Trace Appendix       |

---

## 4 Pre-Flight Sequence

1. **Validate files** — ensure `CONTENT_MAP.(md|docx)` exists and conforms (else **E01**).
2. **Validate source corpus** — attempt extraction for each file; emit **E02** for any failure.
3. **Parse Content-Map** — confirm exactly eight distinct `Module ID`s unless `module_id` subset supplied.
4. **Lock SHA‑256 hashes** of the entire map plus course-level metadata.
5. **JSON Handshake** — immediately output:

```json
{
  "handshake": {
    "timestamp": "2025-06-06T12:00:00Z",
    "content_map_found": true,
    "module_count": 8,
    "hashes_locked": true,
    "ready_to_proceed": true
  }
}
```

If any flag is `false`, emit **E03** and halt.

---

## 5 Per-Module Processing Loop

_(Runs for each Module ID in ascending order, or the subset specified in `module_id=`)_

### 5.1 Data Mining

- Re-process **all source files**.
- Filter to content relevant to this module’s _Key Topics_ and _Sub-topics_.
- Respect 15 000-character chunk ceiling.

### 5.2 Layer Pipeline

| Layer                          | Module leveraged (from _Adobe_FRE_mini_omni_Supporter.md_)          | Mandatory outputs                                                              |
| ------------------------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **L1 Foundation**              | `Learner_Outcomes_Module`                                           | Refined objectives & misconception list                                        |
| **L2 Content Dev.**            | `Learning_Activity_Generator_Module` + `Misconception_Check_Module` | Concept explanation, real-world example(s), visual asset brief, two activities |
| **L3 Scaffolding & Alignment** | `Differentiation_Scaffolding_Module` + `Pedagogy_Module`            | Support & stretch adaptations; Bloom / Gagné / ARCS tags                       |
| **L4 QA**                      | `Accessibility_Module` (+ `image_gen` if `ASSET_GEN=true`)          | WCAG fixes; asset URLs                                                         |

### 5.3 Module Package Output (strict Markdown)

```markdown
### Module <ID> — <Module Title> (<Duration>)

**Topic ➞ Sub-topic:** <from Content-Map>

| Section                             | Content                                     |
| ----------------------------------- | ------------------------------------------- |
| Objectives (refined)                | EXAMPLE_CONTENT                             |
| Concept Explanation                 | EXAMPLE_CONTENT                             |
| Real-world Example                  | EXAMPLE_CONTENT                             |
| Visual Asset                        | Brief: EXAMPLE_CONTENT URL: EXAMPLE_CONTENT |
| Activity 1 (Core)                   | EXAMPLE_CONTENT                             |
| Activity 2 (Extension)              | EXAMPLE_CONTENT                             |
| Misconception Check                 | EXAMPLE_CONTENT                             |
| Differentiation (Support / Stretch) | EXAMPLE_CONTENT                             |
| Timing Table (min)                  | Intro • Explain • Activity • Debrief        |
| Reflection Prompt                   | EXAMPLE_CONTENT                             |
| Extra Resources                     | EXAMPLE_CONTENT                             |
| Instructor Notes                    | EXAMPLE_CONTENT                             |
```

_One table per **Topic**; concatenate within the module._  
If the package exceeds 3 000 tokens → **E05**.

### 5.4 Source-Trace Appendix

```markdown
#### Source-Trace Appendix — Module <ID>

| Concept Section     | File                 | Page/Slide | Hash-snippet          | Citation     |
| ------------------- | -------------------- | ---------- | --------------------- | ------------ |
| Concept Explanation | onboarding_deck.pptx | 12         | fe12abEXAMPLE_CONTENT | (Smith 2024) |
| Real-world Example  | use-cases.pdf        | 7          | 98bca3EXAMPLE_CONTENT | (Smith 2024) |
```

Generate one row per Concept Explanation & Example; citation style per `CITATION_STYLE`.  
Missing row → **E12**.

### 5.5 Readability Gate

Run `Readability_Module`; fail with **E11** if Grade > 10.

---

## 6 Post-Loop Aggregation

1. **Agenda Table** — Module ID | Title | Total minutes.
2. **Master Glossary** — deduplicate & alphabetise mined key terms across all modules.
3. **Re‑hash & verify** locked data (fail **E08**).
4. **Duplicate scan** across module packages (fail **E09**).
5. **Accessibility Final‑Check** on whole document (fail **E04**).

---

## 7 Output Schemas & Budgets

- Module package table must match §5.3 exactly (else **E06**).
- Source‑Trace Appendix table must match §5.4 exactly (else **E06**).

Token targets:

- ≤ 150 tokens per Topic table row.
- Source‑Trace + Glossary + Agenda combined ≤ 6 000 tokens.

---

## 8 Export Standards

Landscape A4 DOCX — 595.28 pt × 841.89 pt; 1 cm margins; sans‑serif 11 pt; header “Course Pack”; footer timestamp + module reference.  
Provide a downloadable link (no inline WordML/XML).  
End document with audit‑trail line.

---

## 9 Parallelised Rerun Procedure

If `module_id=[...]` is supplied, execute full §5 loop **only** for those IDs; skip others. All global gates (§6) still run.

---

## 10 Chunk‑Handling & Fallback Extraction

Use the same extraction rules as in the “Unified Content‑Map” prompt v 3.4. Unsupported MIME → plain‑text fallback; if unreadable → **E02**.

---

## 11 Error‑Handling Summary

On failure, output **only** a bullet‑list of error codes plus description.  
If **E01** occurs, append: “Please attach a valid Content‑Map file (Layer 1 & Layer 2) and rerun.”

---

_End of prompt._

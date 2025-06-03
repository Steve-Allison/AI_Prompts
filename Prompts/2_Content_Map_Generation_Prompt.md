# Content_Map_Generation_Prompt

Version 1.0
---

## GLOBAL INSTRUCTIONS

1. **System State & Language**

   - Clear all memory and cached state before execution; always start from a clean slate.
   - Use British English spelling and punctuation throughout.

2. **Module Integration & Output Routing**

   - **Mandatory:** Adhere to the Meta-Prompt:
     - Use the **summary output (“Layer 1”) from the Learning_Activity_Generator_Module** for the “Activities / Assessments” column in the Content Map table.
     - Use the **detailed output (“Layer 2”)** as an appendix in the exported document, referenced by module/topic.
     - Never combine, truncate, or remix these outputs unless specifically instructed and approved by SME/reviewer.
   - All activities, objectives, and outcomes must be traceable to the Learner_Outcomes_Module and validated for theory alignment (Bloom, Gagné, Kirkpatrick, ARCS).
   - All outputs must comply with export standards (A4 Landscape, British English, Sans-serif 11 pt+, 1.5 cm margins, footer with timestamp, page numbers, and module reference).

3. **Validation & Error Handling**
   - Validate presence and completeness of all required input modules and required fields before any generation.
   - If any module or field is missing, output a clear HTML bullet list of missing/invalid items and halt execution. Prompt for the user to upload AI Prompt MODULES – ALL.pdf if modules are missing.
   - Log a validation summary (pass/fail list) before proceeding with generation.
   - Do not proceed with partial or incomplete data.

---

## CONTENT MAP GENERATION PROMPT

### OBJECTIVE

Generate a high-integrity, fully instructional, measurable, and SME-ready Content Map (visual curriculum plan) for a course, ensuring:

- Alignment of time, activities, goals, objectives, and outcomes across all sessions.
- All elements are mapped to validated learning outcomes and theory.

### REQUIRED INPUT MODULES (Validated Before Execution)

| Module                             | Description                                                                |
| ---------------------------------- | -------------------------------------------------------------------------- |
| MODULE_INFO_DOC                    | Structured course outline (1.1.1–1.2.X.X)                                  |
| Learner_Outcomes_Module            | Generates/validates Gaps, Goals, Objectives & Outcomes (GGOO)              |
| pedagogy_module                    | Validates theory alignment: Bloom, Gagné, Kirkpatrick, ARCS, accessibility |
| Learning_Activity_Generator_Module | Generates/validates activities; summary for table, detailed for appendix   |
| CONTENT_MAP_INSTRUCTIONS_DOC       | Governs table structure & export guidelines                                |

- **If any module is missing, halt and prompt for correction/upload.**

### REQUIRED FIELD VALIDATION (From MODULE_INFO_DOC)

- 1.1.1 – Course Title
- 1.1.2 – Modality
- 1.1.3 – Target Audience
- 1.1.4 – Total Course Duration
- 1.1.5 – Learning Goal (macro)
- 1.1.6.X – Module Learning Objectives
- 1.2.X.X – Topics & Sub-topics (time, format, tools, assessments)
- **Each 1.2.X.X entry must map one-to-one with Key Topics/Time-Split in the Content Map.**

---

## EXECUTION SEQUENCE

1. **Validate** all modules and field completeness.
2. **Generate Topic-Intent statements** from 1.2.X.X (using Topic_Sentence_Expander, if EXPAND_TOPICS = yes).
3. **Generate and validate Learning Gaps & Learning Goal** (via Learner_Outcomes_Module).
4. **Generate SMART Learning Objectives** aligned to Topic-Intent statements.
5. **Generate measurable Learning Outcomes** aligned to Objectives.
6. **Apply instructional alignment tags** (Bloom, Gagné, Kirkpatrick, ARCS).
7. **Generate Activities & Assessments** (summary for Content Map table, detailed for appendix—see Global Instructions).
8. **Map Topics & Time-Split** from MODULE_INFO_DOC.
9. **Assemble and format the Content Map table**.
10. **Export** as .docx, including appendices and compliance with style/export standards.

---

## OUTPUT FORMAT

### Header (Course Details)

- Course Title, Generation Date, Modality, Target Audience, Total Duration, Module Learning Goal, Module Learning Objectives (macro-level).

**Content Map Table**
| Module | Duration & Time‑Split | Key Topics (Topic‑Intent) | Learning Objectives | Activities / Assessments | Learning Outcomes | Instructional Alignment |

- Activities/Assessments: **Use summary output (“Layer 1”) from Learning_Activity_Generator_Module.**
- Instructional Alignment: List Bloom, Gagné, Kirkpatrick, ARCS tags per row.

### Appendix

- **Include detailed activity output (“Layer 2”) from Learning_Activity_Generator_Module, referenced by module/topic.**
- Include any validation/traceability appendices as required by pedagogy_module and learner_outcomes_module.

### Export Style

- British English, A4 Landscape (29.7 × 21.0 cm), 1.5 cm margins, Sans-serif 11 pt+, footer with timestamp, course title, page numbers, reference to AI Prompt MODULES – ALL.pdf.

---

## EFFICIENCY OPTIMISATIONS

1. **Modularise Repeated Logic:**

   - Reference global validation and output routing logic once, at the start, and do not repeat in module-specific steps.
   - Each module’s sub-prompts should refer back to the consolidated “Global Instructions” instead of restating logic.

2. **Minimise Redundant Validations:**

   - Perform field and module validation _once_ at the beginning; avoid repeated checks unless context changes (e.g., re-run with new data).

3. **Auto-generate Missing Inputs When Possible:**

   - Where allowed, if minor GGOO elements or topic-intent statements are missing and can be reliably inferred, auto-generate drafts but flag for SME review, rather than halt on small gaps.

4. **Parallel Module Execution:**

   - If platform permits, allow independent modules (like activity generation, objective validation, and pedagogy tagging) to process in parallel after successful field validation.

5. **Pre-define Table/Template Structures:**

   - Store and reference pre-approved table formats for output, reducing rendering and formatting logic in the prompt.

6. **Version & Change Tracking in Output:**

   - Auto-append version/change history, reviewer notes, and validation logs at the end of the output, rather than scattering throughout the document.

7. **Parameterise Export Controls:**

   - Set variables for export parameters (page size, margins, font, etc.) once at the start, referenced by all downstream steps/modules.

8. **Summary and Appendix Linking:**

   - Automatically generate links from each Content Map row (in the Activities/Assessments column) to the corresponding detailed activity in the appendix, for fast SME navigation.

9. **Clear Separation of Logic & Content:**

   - Keep “how to do it” (logic) in the prompt, and “what to output” (content) in the tables/fields, for clarity and easier updates.

10. **Batch Error Reporting:**
    - Aggregate all missing/invalid fields/modules in a single HTML bullet list for user correction, rather than reporting one at a time.

---

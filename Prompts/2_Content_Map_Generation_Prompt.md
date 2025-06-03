# Content_Map_Generation_Prompt

Version 1.1

## INSTRUCTIONS

- Use British English. Clear memory/cache before execution.
- **Layer 1: Content Map Table**
  - Generate a table: Module | Duration | Key Topics | Learning Objectives | Activities/Assessments (Layer 1 summary only) | Learning Outcomes | Instructional Alignment (Bloom, Gagné, Kirkpatrick, ARCS).
  - No detailed instructions, differentiation, accessibility, visuals, or asset plans in this table.
  - Activities: Use summary output from Learning_Activity_Generator_Module only.
  - All items must trace to Learner_Outcomes_Module and have theory alignment.
  - Follow export standards (A4 Landscape, Sans-serif 11 pt+, margins, footer with timestamp, page numbers, module ref).

- **Layer 2: Appendix**
  - For each activity/assessment in Layer 1, include detailed output from Learning_Activity_Generator_Module (Layer 2), referenced by module/topic.
  - Include detail from Differentiation_Scaffolding_Module, Accessibility_Module, and Misconception_Check_Module in the appendix only.
  - Optionally add threshold concepts and high-priority misconceptions for SME review.
  - Do not remix outputs unless SME-approved.

- **Validation**
  - Before generation, validate all required modules and fields; halt and report missing items in a single bullet list if incomplete.

## EXECUTION SEQUENCE

1. Validate modules/fields.
2. Expand topic-intent statements as needed.
3. Generate and validate gaps, goals, objectives, outcomes (via Learner_Outcomes_Module).
4. Align to theory tags.
5. Generate activities/assessments: summary for table, detail for appendix.
6. Map topics/duration.
7. Assemble/export table (Layer 1) and appendix (Layer 2) as .docx per export standards.

## OUTPUT

**Header:** Course details (title, date, modality, audience, duration, goal, objectives).

**Layer 1 Table:** Module | Duration | Key Topics | Learning Objectives | Activities/Assessments | Learning Outcomes | Instructional Alignment

**Appendix:** Layer 2 activity details, differentiation, accessibility, misconceptions, and SME references only.

---

*Optimise by modularising validation and error reporting, and parameterising exports globally.*

# Learning_Activity_Generator_Module

Version: 1.2

---

## 1. Purpose

Generate, QA, and document fully scaffolded, accessible learning activities for adult learners, mapped to learning objectives, traceable to theory, and ready for review or implementation.

**Outputs:**

- **Layer 1:** Activity Summary for review/signoff
- **Layer 2:** Detailed Activity Guide for instructors/facilitators
- **Differentiation Options:** (Standard, Challenge, Scaffolded/Support versions if requested)
- **Choice Board:** (Menu of activity formats if requested)
  Requester can specify any or all outputs.

---

## 2. Inputs

- **course_content / resources** (optional; for content-aware activity suggestions)
- **learning_objectives** (required)
- **skill_area / topic** (e.g., product knowledge, presentation skills)
- **delivery_mode** (synchronous, asynchronous, blended)
- **assessment_type** (formative, summative)
- **interaction_type** (individual, peer, group)
- **persona_context** (tailor for audience relevance, difficulty, engagement)
- **cue/tag_metadata** (optional; to trigger reflective/generative/scaffolded tasks)
- **reviewer/SME_notes** (for audit, versioning)
- **previous_version** (for change tracking)
- **output_detail_level**: "summary", "detailed", or "both" (default: "both")
- **learner_profile_data** (optional; for advanced personalization)
- **activity_constraints/preferences** (optional; e.g., group size, tech, resource limits, language level)
- **differentiation_level** (optional; e.g., "standard", "challenge", "scaffolded")
- **export_format** (optional; e.g., Google Classroom, SCORM, PDF, DOCX, xAPI)

---

## 3. Workflow & Instructional Logic

### 3.1 Step 1: Input Readiness

- If **learning objectives** are missing or unclear, call **learner_outcomes_module** to generate/refine.
- Halt and prompt for any other missing required fields.

### 3.2 Step 1.5: Personalization & Differentiation

- If learner_profile_data or differentiation_level is provided, suggest or generate Standard, Challenge, and Scaffolded/Support versions of the activity, adjusting complexity/support as needed.
- If activity_constraints/preferences are set, adapt all activity suggestions to those constraints (e.g., low-tech, short time, group size).

### 3.3 Step 2: Activity Generation

- **2.1 Content Analysis (if course content/resources supplied):**

  - Call **content_analysis_module** to extract key skills, themes, and contextual factors from provided materials.
  - Use insights to inform activity format suggestions.

- **2.2 Activity Ideation:**

  - Based on all content, objectives, and inputs (including content analysis if run), suggest 2–3 alternative, instructionally aligned activity formats (e.g., scenario analysis, simulation, role-play, debate, peer review, group project, reflective journal, etc.), mapped to learning objectives and learner context.
  - Summarize each option in 1–2 sentences and **state estimated duration/timing for each**.
  - Optionally, present as a **choice board** for learner/SME selection.

- **2.3 Student Voice / Co-Creation:**

  - Suggest one student voice or co-creation opportunity per activity (e.g., "Invite learners to help design the peer assessment rubric.")

- **2.4 Selection:**

  - Allow the user or SME/reviewer to select the preferred activity format, or auto-select the best match if no preference is given.

- **2.5 Activity Drafting:**

  - Generate the full activity (summary, detailed, and any differentiation/choice board as per inputs) for the selected format, **including estimated timings for each step**.
  - For each activity, output a "Why this works" research/theory-based impact statement.
  - Generate adaptive reflection prompts linked to the theory/level.
  - Output a readiness/practical requirements checklist and a "Plan B" contingency for live/tech-based formats.

### 3.4 Step 3: Cue Tagging

- Call **cognitive_keyword_watchlist_module** to auto-tag cues, reflection prompts, theory references, and access notes.

### 3.5 Step 4: QA, DEI Audit, and Analytics Tagging

- Call **learning_theories_checklist_module** (outputs: QA table, summary, remediation log).
- Call **pedagogy_module** for alignment, accessibility, traceability validation (outputs: validation table, traceability appendix).
- **Accessibility & DEI Review:**

  - Audit for inclusive language, cultural bias, and diversity of examples (prompt for revision if any issues).
  - Require use of diverse names, contexts, and global perspectives in cases/examples.

- **Analytics Tagging:**

  - Tag each activity with learning analytics-ready labels (e.g., "collaborative", "critical thinking", "simulation").

- If issues/remediation required, block export and notify requester.

### 3.6 Step 5: Asset Planning (Optional)

- If digital/physical assets are required (e.g., worksheet, slides), call **learning_asset_module** to generate asset table and reviewer notes.

### 3.7 Step 6: Reviewer/SME Customization and Output Compilation

- Provide co-creation fields for SME/facilitator to add local notes, cohort-specific adaptations, or regulatory requirements.
- Integrate QA/validation results and reviewer checklists into final outputs.
- Include full audit trail/version log with summary of what changed and why.
- Add regulatory compliance checklist if required by context.

### 3.8 Step 7: Continuous Feedback Loop

- After the activity is delivered, prompt the instructor/facilitator to submit feedback (e.g., on learner engagement, outcomes, improvements).
- Call **feedback_module** to log/analyse this input for continuous improvement and versioning.

### 3.9 Step 8: Export/Integration

- Output in user-specified format(s); support for batch generation and LMS-ready export if requested.

---

## 4. Outputs

### 4.1 Activity Summary (Layer 1)

| Field                 | Example                                                      |
| --------------------- | ------------------------------------------------------------ |
| Activity Title        | Peer Demo Feedback                                           |
| Objectives            | Apply presentation skills                                    |
| Mode                  | Synchronous (Live)                                           |
| Assessment Type       | Formative (Peer/Instructor Feedback)                         |
| Brief Description     | Learners present demos; peers give feedback                  |
| Key Theory Alignment  | Bloom: Apply, Gagné: Practice, ARCS: Relevance               |
| Accessibility Summary | Captions for all prompts, flexible formats                   |
| Reviewer Notes        | Needs timer for feedback; v2, 2024-06-06                     |
| Cue Tags (auto)       | Reflection, Peer Review, Active Learning                     |
| Preconditions         | Presentations prepped, feedback sheet ready                  |
| Estimated Duration    | 30 minutes total                                             |
| Differentiation       | Standard, Challenge, Scaffolded versions available           |
| Choice Board          | Project / Case Study / Panel Discussion                      |
| Analytics Tags        | collaborative, peer assessment, critical thinking            |
| DEI Review            | Diverse names, examples, global context                      |
| Student Voice         | "Learners help set criteria for peer feedback"               |
| Readiness Checklist   | Tech: Zoom, Docs; Materials: Feedback forms; Group size: 3–4 |
| Plan B                | If Zoom fails, use paper forms in roundtable                 |
| Impact Statement      | "Peer review boosts engagement and relevance."               |
| Version/Change Log    | v2, 2024-06-06                                               |

---

### 4.2 Detailed Activity Guide (Layer 2)

- **Estimated Duration:** State total time and duration for each step.
- **Step-by-Step Instructions:**

  1. Setup room (5 min) and distribute feedback worksheets.
  2. Divide learners into groups of 3–4 (2 min).
  3. Each learner gives a 3-min demo (15 min total).
  4. Peers complete feedback forms after each presentation (5 min).
  5. Group discusses main feedback themes (5 min).
  6. Instructor facilitates a closing reflection and records key takeaways (3 min).

- **Facilitator Script:**
  “Welcome to the peer feedback session...”
- **Learner Instructions:**
  “As your peers present, complete the feedback worksheet focusing on clarity and engagement..."
- **Differentiation/Adaptation:**

  - Standard: as above
  - Challenge: require self-critique and video submission
  - Scaffolded: use feedback sentence starters, extra time, or paired practice

- **Editable Worksheets:**
  \[Link to Google Doc] | \[Download MS Word]
- **Assessment Rubric:**

  | Criteria   | Exemplary | Satisfactory | Needs Improvement |
  | ---------- | --------- | ------------ | ----------------- |
  | Clarity    | ...       | ...          | ...               |
  | Engagement | ...       | ...          | ...               |

- **Accessibility & UDL Checklist:**

  - Captioning required for presentations
  - Worksheets provided in accessible format
  - Visual prompts described verbally

- **Tool/Platform Guide:**

  - Zoom breakout rooms for online
  - Google Docs or paper forms for feedback

- **Adaptation Matrix:**

  | Mode      | Tech Required | Adaptation Notes        |
  | --------- | ------------- | ----------------------- |
  | In-person | None          | Use printed forms       |
  | Remote    | Zoom, Docs    | Use shared digital docs |

- **Reflection Prompts:**

  - “What’s one change you’ll make after today’s feedback?”
  - “Where else can you use peer feedback skills?”

- **Theory & Rationale:**

  - Activity is grounded in Bloom (Apply), Gagné (Elicit Performance), and Knowles’ andragogy (peer relevance, autonomy).

- **DEI Review:**

  - Case examples use global/diverse contexts; bias/inclusive language checked.

- **Student Voice:**

  - “Invite learners to help design the peer rubric.”

- **Readiness Checklist:**

  - Tech: Zoom/Docs; Materials: Feedback forms; Group size: 3–4.

- **Plan B:**

  - “If tech fails, use paper feedback and roundtable discussion.”

- **Analytics Tags:**

  - collaborative, peer assessment, critical thinking

- **SME/Facilitator Customization Field:**

  - "Add local notes or case examples here."

- **Change Log/Reviewer Actions:**

  - v2: Timer added; worksheet revised for accessibility
  - Reviewer: SME approval pending, June 2024

---

### 4.3 QA/Validation Tables & Reviewer Checklist

- **learning_theories_checklist_module Output:** QA Table (all mapped taxonomies/theories, pass/fail, remediation)
- **pedagogy_module Output:** Validation table, accessibility flags, traceability notes
- **Reviewer Checklist:**

  - Activity mapped to objective and theory?
  - Accessibility/UDL requirements met?
  - All reviewer comments addressed?
  - DEI/Inclusive Language passed?
  - Remediation required?

---

### 4.4 Asset Table (Optional, if assets needed)

| Asset Type | Description        | Accessibility  | Reviewer Notes | Export Instructions |
| ---------- | ------------------ | -------------- | -------------- | ------------------- |
| Worksheet  | Peer feedback form | Accessible PDF | Reviewed v2    | Upload to LMS       |
| Slides     | Reflection prompts | Alt text       | Pending SME    | For session end     |

---

## 5. Error Handling

- If objectives/assessment/delivery mode missing, **halt and prompt**.
- If accessibility/theory QA/DEI fails, **flag and block export until resolved**.
- Log all reviewer feedback and remediation in version history.

---

## 6. How to Use

- **Specify:** output_detail_level = "summary", "detailed", or "both"
- **Provide:** all required input fields
- **Request differentiation, choice board, export format, or batch as needed**
- **Receive:** the desired output(s) with built-in QA, reviewer fields, and ready-to-use guides/templates

---

## 7. Module Integration Table

| Function                        | Module Called                      | Output Used In                   |
| ------------------------------- | ---------------------------------- | -------------------------------- |
| Objective generation/refinement | learner_outcomes_module            | Activity Table                   |
| Content analysis                | content_analysis_module            | Activity Ideation                |
| Cue tagging & metadata          | cognitive_keyword_watchlist_module | Cue Tags, Metadata               |
| Learning science QA/validation  | learning_theories_checklist_module | QA Table, Remediation            |
| Pedagogy/alignment validation   | pedagogy_module                    | Validation Table                 |
| Asset planning (if required)    | learning_asset_module              | Asset Table                      |
| Continuous feedback             | feedback_module                    | Activity improvement, versioning |

---

## 8. Sample User Prompt

> “Generate a learning activity for presentation skills, synchronous delivery, formative assessment, peer group interaction. Please provide standard, challenge, and scaffolded versions as a choice board, include student voice options, and export as both PDF and DOCX.”

---

**This is the advanced, QA-validated, and inclusive Learning_Activity_Generator_Module, ready for any modern LxD workflow!**

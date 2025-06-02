# Learning_Asset_Module

**Version: 1.2**

---

## Purpose

This module provides a best practice logic layer to support AI prompts or other modules tasked with creating multimedia learning assets. It defines how assets should be: to support AI prompts tasked with creating multimedia learning assets. It defines how assets should be:

- Aligned with the **learning objectives and instructional context**
- Informed by **pedagogical principles** and **learning design best practices**
- Output in formats that are **accessible, editable, and stylistically consistent**
- Informed by separate **style**, **tone**, or **structure** modules when explicitly included

---

## Function

This module should be embedded into prompts where the AI is expected to:

1. **Analyse instructional inputs** (script, objectives, storyboard, or wireframe)
2. **Decide what type of asset best suits the goal**
3. **Incorporate external style/pedagogy modules** when available
4. **Output a design plan or draft asset** using approved formats

---

## Expected Inputs

| Input                          | Description                                                                                   | Required?   |
| ------------------------------ | --------------------------------------------------------------------------------------------- | ----------- |
| learning_objectives          | A list of instructional goals                                                                 | ✅ Required |
| script_content               | A passage or lesson segment                                                                   | ✅ Required |
| storyboard                   | Optional visual sequence or structure                                                         | Optional    |
| wireframe                    | Optional layout guidance or slide framework                                                   | Optional    |
| Visual_Style_Module          | Optional visual identity ruleset (e.g. Corporate Minimal v1.0)                                | Optional    |
| pedagogy_module              | Optional learning theory guidance (e.g. Mayer, Bloom, Merrill)                                | Optional    |
| cognitive_watchlist          | List of flagged key terms requiring visual emphasis or explanation                            | Optional    |
| cognitive_watchlist_detailed | Keyword objects with type, load, clarity, and objective links (for enhanced visual treatment) | Optional    |
| intent_tags                  | Thematic or strategic framing cues (e.g. empathy, urgency, confidence)                        | Optional    |
| delivery_channel             | Target platform or format (e.g. mobile, LMS, PDF, facilitator)                                | Optional    |
| Tone_of_Voice_Module         | Defines emotional tone and linguistic framing (e.g. assertive, compassionate)                 | Optional    |
| Accessibility_Module         | Visual compliance rules for contrast, alt text, font scaling, and DEI                         | Optional    |
| feedback_enabled             | Boolean: if true, enables asset suggestion prompts and output clarification steps             | Optional    |

| Input                   | Description                                                            | Required?     |
| ----------------------- | ---------------------------------------------------------------------- | ------------- |
| learning_objectives   | A list of instructional goals                                          | ✅ Required   |
| script_content        | A passage or lesson segment                                            | ✅ Required   |
| storyboard            | Optional visual sequence or structure                                  | Optional      |
| wireframe             | Optional layout guidance or slide framework                            | Optional      |
| Visual_Style_Module   | Optional visual identity ruleset (e.g. Corporate Minimal v1.0)         | Optional      |
| pedagogy_module       | Optional learning theory guidance (e.g. Mayer, Bloom, Merrill)         | Optional      |
| cognitive_watchlist   | List of flagged key terms requiring visual emphasis or explanation     | Optional      |
| intent_tags           | Thematic or strategic framing cues (e.g. empathy, urgency, confidence) | Optional      |
| delivery_channel      | Target platform or format (e.g. mobile, LMS, PDF, facilitator)         | Optional      |
| ----------------------- | ----------------------------------------------------------------       | ------------- |
| learning_objectives   | A list of instructional goals                                          | ✅ Required   |
| script_content        | A passage or lesson segment                                            | ✅ Required   |
| storyboard            | Optional visual sequence or structure                                  | Optional      |
| wireframe             | Optional layout guidance or slide framework                            | Optional      |
| Visual_Style_Module   | Optional visual identity ruleset (e.g. Corporate Minimal v1.0)         | Optional      |
| pedagogy_module       | Optional learning theory guidance (e.g. Mayer, Bloom, Merrill)         | Optional      |
| cognitive_watchlist   | List of flagged key terms requiring visual emphasis or explanation     | Optional      |

---

## Logic Rules

> ### Rule 10: Tone Integration
>
> If Tone_of_Voice_Module is provided, adapt embedded text, character/dialogue tone, and visual metaphors to reflect the specified emotional framing (e.g. assertive → arrows; compassionate → supportive icons). Ensure harmony with any style guidance.

> ### Rule 11: Accessibility Compliance
>
> If Accessibility_Module is present, asset output must:
>
> - Use compliant colour contrast and readable fonts
> - Include descriptive alt text for all visual elements
> - Provide non-verbal equivalents where appropriate (e.g. icon labels, transcripts)

> ### Rule 12: Feedback Loop Support
>
> If feedback_enabled = true, return optional:
>
> - Follow-up prompts to refine tone or structure
> - Asset alternatives with reasoning
> - Suggestions for adaptation into other media or platforms

> ### Rule 1: Input Validation
>
> If learning_objectives and script_content are not provided, return: _"Missing required inputs: cannot generate asset without both objectives and content context."_

> ### Rule 2: Input Integration
>
> If storyboard or wireframe are present, analyse them alongside the script and objectives to identify the intended sequence, framing, or asset flow.

> ### Rule 3: Format Recommendation
>
> Based on all valid inputs, infer the most appropriate asset format (e.g. static visual, diagram, scenario, animation frame) and explain the rationale.

> ### Rule 4: Optional Module Use
>
> - If Visual_Style_Module is present: apply it strictly
> - If not: use default minimalist, instructional layout
> - If pedagogy_module is present: prioritise asset structure accordingly
> - If not: default to Mayer’s coherence and signalling principles

> ### Rule 5: Output Specification
>
> Return the asset plan using this structure:
>
> - Asset Type & Title
> - Purpose and Learning Objective it Supports
> - Visual / Structural Description
> - Layout & Format Recommendation
> - Export Instructions (PDF with fonts embedded; no outlines; PNG if bitmap)

> ### Rule 6: Cognitive Highlighting (Enhanced)
>
> If cognitive_watchlist_detailed is provided, the asset must:
>
> - Match each term with its keyword_type and apply corresponding treatments:
>
>   - **concept** → diagram element or icon
>   - **skill** → scenario or action-based visual
>   - **emotion** → tone or character cue
>   - **myth/misconception** → counter-example, tooltip, or red flag icon
>
> - Prioritise terms where clarity_required = true for explicit visual labelling
> - If cognitive_load = high, use visual chunking and minimise surrounding visual clutter
> - Collaborate with Visual_Style_Module and pedagogy_module for consistent expression
>
> If only cognitive_watchlist is present, apply simplified emphasis (e.g. label, icon, callout).

> ### Rule 7: Intent Mapping
>
> If intent_tags are provided, the asset must:
>
> - Choose formats, layouts, or narrative framing that reinforce the intended tone (e.g. empathy → scenario; urgency → timeline)
> - Coordinate tone elements with any connected Visual_Style_Module or Tone_of_Voice_Module

> ### Rule 8: Asset Variation Suggestion
>
> If multiple approaches are suitable, propose:
>
> - One primary asset format
> - One alternative (with rationale for different learner needs, modalities, or delivery environments)

> ### Rule 9: Delivery Adaptation
>
> If delivery_channel is provided, the asset format and layout must accommodate that context (e.g. mobile-first sizing, printable layout, facilitator annotation zones)

---

## Example Use Case

**Inputs Provided:**

- learning_objectives: \["Apply the AIDA model to persuasive writing"]
- script_content: "In this segment, learners explore Attention, Interest, Desire, and Action as a method for structuring compelling arguments."
- intent_tags: \["persuasion", "confidence"]
- cognitive_watchlist: \["Attention", "Interest", "Desire", "Action"]
- Visual_Style_Module: "Corporate Minimal v1.0"
- delivery_channel: "LMS slide"

**Output (From this Module):**

- **Asset Type**: Infographic
- **Title**: "The AIDA Model in Action"
- **Learning Objective Supported**: Apply the AIDA model to persuasive writing
- **Description**: A 16:9 slide with a four-step diagram. Each section uses a muted colour and includes a short description, with subtle emphasis on key terms ("Attention", etc.) using icons and tone-consistent highlights.
- **Format**: PDF (vector, embedded fonts); designed for LMS slide delivery

---

## Cross-Module Integration

### Mapping from Learning_Activity_Generator_Module

| Output Field from Activity Generator | Mapped Input in This Module                             |
| ------------------------------------ | ------------------------------------------------------- |
| activity_objective                 | learning_objectives                                   |
| activity_script                    | script_content                                        |
| activity_storyboard                | storyboard                                            |
| activity_layout_notes              | wireframe                                             |
| preferred_delivery_channel         | delivery_channel                                      |
| instructional_tone                 | Tone_of_Voice_Module                                  |
| accessibility_requirements         | Accessibility_Module                                  |
| activity_keywords                  | cognitive_watchlist or cognitive_watchlist_detailed |

### Mapping from Cognitive_Keyword_Watchlist_Module

| Output Field from Watchlist Module             | Mapped Input in This Module    |
| ---------------------------------------------- | ------------------------------ |
| keywords (simple list)                       | cognitive_watchlist          |
| keywords_detailed (with type, load, clarity) | cognitive_watchlist_detailed |

This module will apply Rules 6, 7, and 10–12 to interpret and integrate cognitive keywords and intent indicators, generating media asset recommendations that reflect both pedagogical purpose and user experience.

---

## Usage Instruction

Embed this module into prompts that must:

- Generate any **learning media asset**
- Ensure alignment with **learning goals**
- Honour **external style/pedagogy constraints**
- Propose the **most appropriate format** for delivery

Activate using:

python
include_module("Learning_Asset_Module")


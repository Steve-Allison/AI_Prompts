# Learning_Theories_Checklist_Module

Version: 1.2

## Purpose:

Serve as a QA and review module to ensure every instructional output (objectives, activities, script segments, cues, and stage directions) is:

- Aligned to proven learning science (Bloom’s Taxonomy, Gagné’s Nine Events, SOLO Taxonomy, Mayer’s Principles, Kirkpatrick, ARCS, Merrill’s First Principles)
- Accessible (meets WCAG and UDL standards; addresses flagged alerts)
- Scaffolded, measurable, and traceable
- Reviewer- and audit-friendly, supporting both automated and human validation
- Extendable through optional advanced theory QA via the Theory_Enhancement_Library module

## Inputs

- Outline Document (1.2.X structure)
- Learning Objectives (user-supplied or auto-generated)
- Script Content (all segments, including cues/tags)
- Cue/Tag Metadata (from Cognitive Keyword Watchlist)
- Accessibility Alerts (flagged by any module)
- Reviewer/SME notes or previous QA status (optional, for revision tracking)

## Outputs
A. Segment-by-Segment QA Table (Designer View)

| Segment | Bloom Level | Gagné Event(s)  | SOLO Level (optional) | Kirkpatrick | ARCS | Alt Text | Captions | Contrast | Navigation | Mayer Principles | Merrill Principle | Generative Activity | QA Status     | Reviewer Note | Remediation Tag | Rewrite Prompt          | Confidence Level | WCAG Tags Present | QA Reviewer | QA Date    | Script Version ID |
| ------- | ----------- | --------------- | --------------------- | ----------- | ---- | -------- | -------- | -------- | ---------- | ---------------- | ----------------- | ------------------- | ------------- | ------------- | --------------- | ----------------------- | ---------------- | ----------------- | ----------- | ---------- | ----------------- |
| 1.2.2   | Apply       | Present, Recall | Multistructural       | L2          | C, S | No       | Yes      | Yes      | Yes        | Coherence        | Activation        | No                  | Action Needed | [Reviewer/AI] | R-ALT           | Add alt text to diagram | Medium           | AltText, Caption  | reviewer1   | 2025-05-24 | v1.0              |
| 1.2.3   | Analyse     | Elicit Perf.    | Relational            | L3          | R    | Yes      | Yes      | Yes      | Yes        | Redundancy       | Application       | Yes                 | Pass          |               |                 |                         | High             | AltText, Caption  | reviewer1   | 2025-05-24 | v1.0              |

B. Global Summary

- Segment-to-objective matrix
- QA pass/fail/attention-needed flag per principle
- Summary checklist:
  - All Gagné events present
  - All segments mapped to Bloom verbs
  - Accessibility checks passed
  - One flagged segment requires remediation
- Accessibility compliance report:
  - Alt Text: 17/18 complete
  - Captions: All complete
  - Visual Contrast: All compliant
  - Navigation: All compliant
- Mayer Principles checklist:
  - Coherence: Yes
  - Redundancy: Yes
  - Signaling: Two segments need headers
- Merrill’s Principles Coverage:
  - Activation: Present
  - Demonstration: Partial
  - Application: Present
  - Integration: Partial
- Remediation/Action Log:
  - [Log with timestamps, actions taken, reviewer initials]

Summary Statement (for audit report)
All 18 segments reviewed. All Gagné events present. 94% of accessibility elements passed. 2 flagged items addressed with remediation. Mayer, Merrill, and ARCS coverage verified. Additional theory tags available in Theory_Enhancement_Library.

C. Appendix (for Audit)

- Full learning theory tag index for each segment and cue
- Version/change log with timestamps and signoff
- Reviewer checklist per learning principle (Bloom, Gagné, SOLO, Mayer, Merrill, ARCS, Accessibility)
- Reviewer signoff fields with editable comments
- Reference to Theory_Enhancement_Library for advanced theory QA

## QA Checks & Rules

Learning Progression

- Every segment maps to a Bloom verb and Gagné event
- Optional: SOLO tag for segments with complex constructivist progression
- Merrill’s principles tagged if present
- No segment over 7 minutes without a chunk, reflection, or generative task
- Kirkpatrick level assigned per activity outcome

Scaffolding

- Model → Support → Challenge (or appropriate adult learning sequence)
- Generative or reflective activity every 5 minutes/pages

Signposting & Personalisation

- Clear “You” language, instructional signposts, and relatable voice

Accessibility

- Alt text for all visuals
- Captions/subtitles for all narrated segments
- High-contrast, accessible fonts and overlays
- Keyboard and touch navigation included for interactives
- WCAG tag traceability in metadata

Mayer’s Principles (Integrated)

- Coherence (remove extraneous material)
- Redundancy (avoid narration and onscreen text duplication)
- Signaling (use headers and visual cues)
- Segmenting (chunked information)
- Modality (visual and spoken narration preferred)

Merrill’s First Principles (Optional)

- Activation
- Demonstration
- Application
- Integration

Motivation (ARCS)
Each segment addresses at least one ARCS factor:

- Attention
- Relevance
- Confidence
- Satisfaction

Pitfall Detection
Flags for:

- Wall-of-text
- Undefined jargon
- Redundant visuals
- Missing reflection/prompt
- Ambiguous cue-to-outcome mapping

Adaptive/Revision Features

Remediation Tags (for automation and reviewer notes)

- R-ALT: Missing alt text
- R-JARGON: Replace or explain unfamiliar terms
- R-REFLECT: Add reflection/prompting
- R-GAGNE: Missing required Gagné event
- R-MAYER: Mayer principle not followed
- R-MERRILL: Merrill principle not applied
- R-ARCS: Missing motivational hook
- R-SIGNPOST: Needs stronger language/personalisation

Reviewer Workflow

- Editable reviewer comment field per QA row
- Automated timestamping and change log versioning
- Reviewer initials and signoff status per principle

Integration

- Feedback and remediation flags exported to:
  - Designer QA table
  - Cue/Tag metadata appendices
  - Script Generator Module (for next-gen rewrite or remediation)
  - Reviewer signoff checklist
- Optional advanced theory QA supported through Theory_Enhancement_Library

Error Handling

- Missing inputs (objectives, script, cues): QA halted and user prompted
- Invalid segment mappings or missing theory tags: flagged for SME review
- Gagné cross-segmental coverage allowed; noted with "Coverage Span"


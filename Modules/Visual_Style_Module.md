# Visual_Style_Module

**Version: 1.3**

---

## Purpose

Define, align, and enforce the visual identity, accessibility standards, instructional design cues, and stylistic coherence of all visual elements—across scripts, assets, presenters, and production workflows.
Ensures cognitive clarity, pedagogical alignment, emotional tone fidelity, accessibility compliance, and brand consistency across all learning assets and outputs.
Enables traceable integration of visual choices with learning theory, tone of voice, cue tagging, and segment-level metadata—supporting scalable review, automation, and quality assurance.

---

## Inputs

- Selected visual style or theme (must reference a registered `Visual_Style_Profile_*` module, e.g., `Visual_Style_Profile_Corporate_Minimal`) (e.g., “Corporate Minimal”)
- Organisation or project branding requirements (optional)
- Accessibility requirements or standards (e.g., WCAG, internal policies)
- Reviewer/SME notes or previous version (for audit/change tracking)

---

## Outputs

### A. Visual Style Profile (fields for review and downstream enforcement)

- **Module Name:** Unique identifier (e.g., “Corporate Minimal”)
- **Visual Aesthetic:** Emotional tone (e.g., “Clean, professional, instructional”)
- **Colour Palette:** Primary and accent colours (with high-contrast, accessibility notes)
- **Typography:** Font family, size, line height, bold/italics rules
- **Layout Format:** Standard aspect ratio, preferred layouts (e.g., 16:9, A4 landscape)
- **Shape Language:** Geometry of boxes, buttons, zones (e.g., rounded rectangles)
- **Iconography Style:** Flat/line icons, minimum stroke/size
- **Illustration Type:** (e.g., flat vector, inclusive avatars, brand-consistent imagery)
- **Image Treatment:** Rules for photos/bitmaps (e.g., “use PNG with transparency, clean cropping”)
- **Character Design:** DEI/inclusivity features, avatar options
- **Tone of Voice (Visual):** Mood/personality of the design (e.g., “Calm, confident, informative”)
- **Visual Tone Consistency Check:** Should match tone tags from Tone_of_Voice_Module (Pass/Flag)
- **Animation & Motion Design Considerations:**

  - Motion Style
  - Allowed Transitions
  - Looping/GIF Use
  - Animation Layers (Y/N)

- **Responsive Layout Guidance:** Optional layouts or restrictions for mobile, tablet, LMS
- **Instructional Alignment Tags (Optional):**

  - Bloom’s Level (e.g., Understand, Apply)
  - Gagné Event (e.g., Presenting stimulus, Providing feedback)
  - ARCS Hook or Attention Tag (e.g., Arousal, Relevance)

- **Cognitive Visual Tagging (Mayer/Instructional Design):** Tags such as "Signalling", "Contiguity", "Modality", etc.
- **Cue Integration Field:** Linked delivery markers or visual cue tags (e.g., \[gesture: open arms], \[confidence_anchor])
- **Scene Metadata Overlay:** Segment ID, emotional tone, Bloom level, delivery marker reference
- **Interaction Type:** Static / Dynamic / Interactive / Responsive
- **Visual_Style_ID:** Format: vs-\[projectname]-\[YYYYMMDD]-vX

---

### B. Accessibility Compliance Fields

- **Accessibility status/alerts for:**

  - High-contrast colours (Pass/Fail, Notes)
  - Alt text guidelines (for all icons, diagrams, complex visuals)
  - Minimum font/size/spacing for readability
  - Inclusive/representative imagery
  - Caption/subtitle support (for any video/text overlays)

- **Reviewer Field: “Accessibility Pass/Action Required”** (Yes/No, with notes)
- **Visual QA Tags (for SME/Accessibility):** Contrast / Captioning / Emotion Fit / Instructional Fit / Tone Match

---

### C. Review/Audit Metadata

- Version/date, reviewer signoff fields
- Change tracking (notes on what’s changed from previous style or visual system)
- SME field for branding or accessibility notes
- **Review Persona Roles:**

  - SME: Branding/tone
  - LxD: Instructional clarity
  - Accessibility Officer: WCAG and inclusivity
  - Visual Designer: Layout/styling

---

## Enrichment and Downstream Use

- **Selected Profile Enforcement:** All visual decisions and downstream modules are governed by the selected `Visual_Style_Profile_*`, which must comply with this parent module structure.
- **Script Generation Module:** Enforces all on-screen assets and keywords to comply with style (font, contrast, brand tone, instructional alignment)
- **Videography_Direction_Module:** Uses framing, background, and on-screen graphics in line with style/brand/instructional tone
- **Cue Tagging/Accessibility Module:** Surfaces when any visual or on-screen element might need alt text, contrast, or adaptation
- **Learning_Asset_Module:** Ensures every visual asset plan meets accessibility, branding, and pedagogical utility requirements
- **Designer Table/Review:** Visual style appendix with all style fields, compliance, reviewer notes, and signoff
- **Revision History:** Tracks style changes and SME/brand approvals

## Error Handling

- If accessibility rules not defined or do not pass auto-check (e.g., insufficient contrast, missing alt text), **flag for review** and halt downstream production.
- If style is ambiguous or non-compliant with brand or tone, **flag for SME revision**.
- If visual tone is inconsistent with narrative tone tags, **surface a consistency flag for Tone_of_Voice_Module cross-check**.

---

## Sample Table (Visual Style Appendix, for Review)

| Field                   | Value                                      | Accessibility Pass | Reviewer Notes                   |
| ----------------------- | ------------------------------------------ | ------------------ | -------------------------------- |
| Module Name             | Corporate Minimal                          | Yes                | New metadata fields added        |
| Colour Palette          | Muted blue/grey, coral accents             | Yes                |                                  |
| Typography              | Arial, 12pt, bold for headings             | Yes                |                                  |
| Icon Style              | Flat, inclusive avatars, min 24x24px       | Yes                | Add alt text for all             |
| Visual Tone Consistency | Matches “calm, confident” tone from script | Yes                |                                  |
| Animation Style         | Subtle fade-in/out only                    | Yes                | Avoid bounce or fast scaling     |
| Cognitive Visual Tag    | Signalling, Modality                       | Yes                | From learning_theories_checklist |
| Interaction Type        | Static                                     | N/A                |                                  |
| Scene Metadata Overlay  | 1.2.3, Empathy, Apply, \[gesture: pause]   | Yes                |                                  |

---

## Checklist for SME/LxD Review

- ✅ Style aligns with current brand and project goals?
- ✅ Visual tone matches script tone?
- ✅ All contrast and alt text guidelines met?
- ✅ Bloom/Gagné/ARCS tags used where helpful?
- ✅ Responsive guidance clear for platform?
- ✅ Reviewer/SME signoff complete?

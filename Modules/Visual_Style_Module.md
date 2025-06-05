# Visual_Style_Module

**v1.3** | Default: `Visual_Style_Profile_Adobe`

## Purpose
Define and enforce visual identity, accessibility, and instructional design standards across all learning assets, ensuring brand consistency, pedagogical alignment, and WCAG compliance.

## Inputs
- Visual style/theme (defaults to `Visual_Style_Profile_Adobe`)
- Branding requirements (optional)
- Accessibility standards (WCAG, etc.)
- Reviewer/SME notes/version history

## Outputs
### Profile Traceability
- Include in metadata: `Visual Style Profile: [Name] | Visual_Style_ID: vs-[project]-[date]-vX`

### A. Visual Style Profile
- **Core Identity**: Name, Aesthetic, Visual_Style_ID
- **Design Elements**: Colors, Typography, Layout, Shapes
- **Assets**: Icons, Illustrations, Images, Characters
- **Motion & Interaction**: Animation style, Responsive rules
- **Instructional Tags**: Bloom's, Gagné, ARCS, Mayer principles
- **Metadata**: Cue tags, Scene data, Interaction type

### B. Accessibility Compliance
- **Checks**: Contrast, Alt text, Readability, Inclusivity, Captions
- **Review**: Pass/Fail status, QA tags (Contrast, Captioning, etc.)

### C. Review Metadata
- Version control, Change log, Reviewer signoffs
- **Review Roles**: SME (Brand), LxD (Instruction), Accessibility, Designer

## Integration
- Enforces style in: Scripts, Videos, Assets, Learning modules
- Tracks revisions and compliance

## Fallback & Error Handling
- Default: `Visual_Style_Profile_Adobe`
- **Flags**: Accessibility issues, Style violations, Tone mismatches

## Sample Style Table
| Field | Value | Access | Notes |
|-------|-------|--------|-------|
| Name | Corporate Minimal | Yes | New fields |
| Colors | Muted blue/grey | Yes | |
| Typography | Arial 12pt | Yes | |
| Icons | Flat, 24px+ | Yes | Add alt text |
| Animation | Fade only | Yes | No bounce |
| Tags | Signalling | Yes | |
| Type | Static | N/A | |

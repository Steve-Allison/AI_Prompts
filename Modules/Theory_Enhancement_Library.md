# Theory_Enhancement_Library

**Version:** 1.0

## Purpose

The Theory_Enhancement_Library is an optional, plug-in module that extends the Learning_Theories_Checklist_Module by providing advanced theory-specific QA prompts, tags, and instructional guidance for situational or less commonly standardized learning models.

It supports:

- Deeper theory coverage for advanced instructional designs
- Modular QA that can be selectively activated
- Alignment with scenario-based, reflective, persuasive, and UX-sensitive learning strategies

---

## Integration Points

### Activation Triggers
- Learning style identification
- Complexity level threshold
- Specific content types (scenarios, simulations, etc.)

### Output Types
- QA prompts
- Tag recommendations
- Remediation suggestions

---

## Supported Theories & Frameworks

### Instructional Design Theories
- 3Cs Scenario-Based Design
- Cathy Moore's Action Mapping
- Mager's ABCD Objectives

### Cognitive & Learning Theories
- Vygotsky's ZPD
- Cognitive Apprenticeship
- Schank's Script Theory

### Motivational & Behavioral Theories
- Monroe's Motivated Sequence
- Nudge Theory
- Gibbs' Reflective Cycle

### Experience & Interface Theories
- LTEM
- Honeycomb UX Model
- Alexander's Dialogue Principles

Each entry below includes:

- Tag format
- Use case/context
- QA checks
- Sample prompt or remediation

#### 1. **3Cs Scenario-Based Design (Challenge, Choice, Consequence)**

- **Tags:** 3C-Challenge, 3C-Choice, 3C-Consequence
- **Use:** Scenario-based modules and simulations
- **QA Prompt:** “Is there a realistic challenge, a meaningful choice, and a visible consequence?”
- **Sample Fix:** “Add a branching path after the learner makes a choice.”

#### 2. **Cathy Moore’s Action Mapping**

- **Tag:** AM-ActionGoal
- **Use:** Performance-based training
- **QA Prompt:** “Does this segment directly support an observable job task?”
- **Sample Fix:** “Refocus segment on what the learner _does_, not what they _know_.”

#### 3. **Mager’s ABCD Objectives**

- **Tags:** ABCD-Audience, ABCD-Behavior, ABCD-Condition, ABCD-Degree
- **Use:** QA for performance-based learning objectives
- **QA Prompt:** “Does the objective specify all four ABCD elements?”

#### 4. **Gibbs’ Reflective Cycle**

- **Tags:** Gibbs-Description, Gibbs-Feelings, Gibbs-Evaluation, Gibbs-Analysis, Gibbs-Conclusion, Gibbs-ActionPlan
- **Use:** Reflective learning (journaling, debriefs)
- **QA Prompt:** “Are all phases of the reflective cycle represented across the module?”

#### 5. **Vygotsky’s Zone of Proximal Development (ZPD)**

- **Tags:** ZPD-Scaffolded, ZPD-Supported, ZPD-Stretch
- **Use:** Challenge calibration and adaptive support
- **QA Prompt:** “Is the task within the learner’s stretch zone, with adequate scaffolding?”

#### 6. **Cognitive Apprenticeship**

- **Tags:** CA-Coach, CA-Model, CA-Fade, CA-Articulate
- **Use:** Mentoring, coaching, or expert modeling contexts
- **QA Prompt:** “Does the design support modeling, coaching, and gradual transfer of control?”

#### 7. **Schank’s Script Theory**

- **Tags:** Script-Initiate, Script-Event, Script-Resolution
- **Use:** Narrative-driven or experience-based instruction
- **QA Prompt:** “Does the narrative reflect a real-world episodic memory structure?”

#### 8. **Monroe’s Motivated Sequence**

- **Tags:** Monroe-Attention, Monroe-Need, Monroe-Satisfaction, Monroe-Visualization, Monroe-Action
- **Use:** Persuasive content and motivation-focused sequences
- **QA Prompt:** “Are all motivational phases logically ordered and linked to the CTA?”

#### 9. **LTEM (Learning-Transfer Evaluation Model)**

- **Tags:** LTEM-Level1 to LTEM-Level8
- **Use:** Evaluation planning and post-learning analytics
- **QA Prompt:** “Is learning transfer measured beyond recall or participation?”

#### 10. **Honeycomb UX Model**

- **Tags:** UX-Useful, UX-Usable, UX-Desirable, UX-Findable, UX-Accessible, UX-Credible, UX-Valuable
- **Use:** UX layer for interactive/multimedia design
- **QA Prompt:** “Does the content meet the full UX honeycomb criteria?”

#### 11. **Nudge Theory**

- **Tags:** Nudge-Prompt, Nudge-Default, Nudge-Social, Nudge-Visual
- **Use:** Subtle motivational cues in UI, copy, or structure
- **QA Prompt:** “Is a non-coercive, behaviorally persuasive cue present?”

#### 12. **Alexander’s Dialogue Principles**

- **Tags:** Dialogue-Reciprocal, Dialogue-Cumulative, Dialogue-Exploratory
- **Use:** Dialogic design in conversation-driven modules
- **QA Prompt:** “Does learner interaction feel reciprocal and exploratory?”

---

## Quick Reference

| Category | Theories | Primary Use Case |
|----------|----------|-----------------|
| Instructional Design | 3Cs, Action Mapping, ABCD | Course structure and objectives |
| Cognitive & Learning | ZPD, Cognitive Apprenticeship, Script Theory | Learning process design |
| Motivational | Monroe's, Nudge, Gibbs | Engagement and reflection |
| Experience & UI | LTEM, Honeycomb, Dialogue | Interface and interaction |

---

## Optional QA Table (Enhancement Overlay)

| Segment | Theory Tag       | QA Prompt                              | Pass/Flag | Reviewer Note             | Suggested Revision                         |
| ------- | ---------------- | -------------------------------------- | --------- | ------------------------- | ------------------------------------------ |
| 1.2.4   | Gibbs-ActionPlan | Is there a prompt for future planning? | Flag      | Add final reflection task | “What would you do differently next time?” |

---

## Usage Notes

- This module is **not required** for every course but can be invoked dynamically by:

  - Reviewer flag
  - Pedagogy_Module design intent
  - AI cue analysis

- Use theory tags consistently across segments and cue metadata
- Link any enhancement feedback back to Remediation Tag column in the core QA module

---

### Versioning & Expansion

Future versions may include:

- Tag sets for additional theories
- Integration with adaptive script generation
- Reviewer workflows or dashboards per theory family

---

**Author:** Steve Allison
**Status:** Active
**Linked Modules:** Pedagogy_Module, Learning_Theories_Checklist_Module, Script Generator Module

[End of Theory_Enhancement_Library module]

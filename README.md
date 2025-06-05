# 🧠 AI Instructional Module Registry

Welcome to the **AI Instructional Modules Registry** — a modular, callable, version-controlled system designed to support AI-driven instructional design, media scripting, accessibility validation, and content enrichment.

---

## 🎯 Project Purpose

This registry defines a modular system of callable AI components for learning design, content generation, accessibility QA, and media scripting. Modules are registered in Markdown and callable via prompt-based tools or orchestration controllers using a consistent interface.

---

## 🧩 Module Overview

### Module Interdependencies

Modules are designed to work together in the following sequence:

1. **Foundation Layer** (run first):

   - `Cognitive_Keyword_Watchlist_Module` - Identifies key concepts and terms
   - `Pedagogy_Module` - Applies learning theories
   - `Tone_of_Voice_Module` - Sets communication style

2. **Content Layer** (run second):

   - `Learning_Activity_Generator_Module` - Creates core activities
   - `Differentiation_Scaffolding_Module` - Adds support and challenge layers
   - `Misconception_Check_Module` - Identifies and addresses learning barriers
   - `Theory_Enhancement_Library` - Adds academic depth

3. **Presentation Layer** (run third):
   - `Visual_Style_Module` - Applies visual design
   - `Accessibility_Module` - Ensures inclusivity
   - `Learning_Asset_Module` - Structures final outputs

Modules are callable using a uniform invocation pattern:

```python
include_module("<Module_Name>")
```

#### 🧱 Module Categories

### Module Reference

| Module Name                          | Function                                                                               | Key Dependencies                                                           |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `Learning_Asset_Module`              | Plans instructional asset format, structure, and layout.                               | `Visual_Style_Module`, `Accessibility_Module`                              |
| `Visual_Style_Module`                | Defines tone-appropriate visual direction and framing.                                 | `Tone_of_Voice_Module`                                                     |
| `Pedagogy_Module`                    | Tags and aligns content to learning theories.                                          | `Cognitive_Keyword_Watchlist_Module`                                       |
| `Tone_of_Voice_Module`               | Aligns voice and delivery tone to emotion and audience.                                | None (foundational)                                                        |
| `Accessibility_Module`               | Applies WCAG and inclusive design adaptations.                                         | `Visual_Style_Module`                                                      |
| `Cognitive_Keyword_Watchlist_Module` | Tracks cognitively/emotionally salient terms and profiles audience engagement.         | None (foundational)                                                        |
| `Video_Script_Generator_Module`      | Generates full instructional scripts from input goals and metadata.                    | `Cognitive_Keyword_Watchlist_Module`, `Tone_of_Voice_Module`               |
| `Learning_Theories_Checklist_Module` | Performs QA checks on pedagogical completeness.                                        | `Pedagogy_Module`                                                          |
| `Instructional_Segment_Mapper`       | Maps segments to structure, role, theory tags, and scaffolding levels.                 | `Cognitive_Keyword_Watchlist_Module`, `Pedagogy_Module`                    |
| `Learning_Activity_Generator_Module` | Generates scaffolded activities aligned to objectives and audience level.              | `Pedagogy_Module`, `Cognitive_Keyword_Watchlist_Module`                    |
| `Theory_Enhancement_Library`         | Supplies contextual academic theory snippets and citations.                            | `Pedagogy_Module`                                                          |
| `Misconception_Check_Module`         | Surfaces, explains, and provides corrective strategies for common misconceptions.      | `Cognitive_Keyword_Watchlist_Module`, `Learning_Activity_Generator_Module` |
| `Differentiation_Scaffolding_Module` | Generates scaffolded supports and extension/challenge activities for diverse learners. | `Learning_Activity_Generator_Module`, `Misconception_Check_Module`         |

### Glossary of Key Terms

- **Scaffolded Support**: Modified versions of activities with additional structure, hints, or resources to support learners who need extra help.
- **Extension/Challenge**: Additional or more complex tasks for learners who have mastered the core content.
- **Formative Question**: A question designed to check understanding and provide feedback during the learning process.
- **Threshold Concept**: A core idea that is essential for understanding a subject but may be challenging for learners.
- **Cognitive Load**: The amount of mental effort required for learning, which should be managed effectively.
- **Pedagogical Alignment**: Ensuring teaching methods match learning objectives and theories.
- **Inclusive Design**: Creating content that is accessible to all learners, regardless of ability or background.

*Note: These terms are aligned with the cognitive and pedagogical definitions embedded in the `Cognitive_Keyword_Watchlist_Module` and `Pedagogy_Module`.*

---

## 🔁 Orchestration & Usage

Modules are designed to be composable in prompt workflows using:

```python
include_module("Module_Name")
```

A typical multi-module orchestration stack may include:

```python
include_module("Video_Script_Generator_Module")
include_module("Pedagogy_Module")
include_module("Tone_of_Voice_Module")
include_module("Learning_Asset_Module")
include_module("Learning_Activity_Generator_Module")
include_module("Storyboard_Generation_Module")
include_module("Accessibility_Module")
include_module("Cognitive_Keyword_Watchlist_Module")
```

---

## 🗂 Structure

Each module is stored as a versioned Markdown specification with the following:

- Purpose
- Callable scope
- Dependencies
- Return fields
- Invocation format
- Version number

---

## 📌 Notes

- Modules are updated through version control.
- This repository supports instructional design teams, AI prompt engineers, and modular orchestration toolchains.
- Extendable via controller logic or metadata frameworks.

---

## 🛠 Contributing

To add a new module, submit a markdown spec following the existing format with:

- A unique name
- A version number (semantic: MAJOR.MINOR.PATCH)
- A clear primary function and return schema

---

## 📄 Licence

This project is licensed for educational, non-commercial use under modular AI registry terms.

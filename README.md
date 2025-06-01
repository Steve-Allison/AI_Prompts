# 📚 AI Instructional Modules Registry

Welcome to the **AI Instructional Modules Registry** — a modular, callable, version-controlled system designed to support AI-driven instructional design, media scripting, accessibility validation, and content enrichment.

---

## 🎯 Project Purpose

This repository provides a centralised, shared registry of AI modules used to orchestrate the generation, enrichment, validation, and layout of multimedia learning experiences.

Each module follows a consistent design pattern and is registered using:

```python
include_module("<Module_Name>")
```

The system is intended to support prompt-based AI tools, controller agents, learning experience designers, and development teams building intelligent content generation workflows.

---

## 🧩 Module Overview

The following modules are registered and version-controlled:

| Module Name                          | Function                                                                                   |
|-------------------------------------|--------------------------------------------------------------------------------------------|
| `Learning_Asset_Module`             | Plans instructional asset format, structure, and layout.                                  |
| `Visual_Style_Module`               | Defines tone-appropriate visual direction and framing.                                    |
| `Pedagogy_Module`                   | Tags and aligns content to learning theories (Bloom, Gagné, ARCS, SOLO, etc.).            |
| `Tone_of_Voice_Module`              | Aligns voice and delivery tone to emotion and audience.                                   |
| `Accessibility_Module`              | Applies WCAG and inclusive design adaptations.                                             |
| `Cognitive_Keyword_Watchlist_Module`| Tracks cognitively/emotionally salient terms and profiles audience engagement.            |
| `Video_Script_Generator_Module`     | Generates full instructional scripts from input goals and metadata.                       |
| `Video_Gold_Structure_Module`       | Validates sequencing and instructional flow of scenes.                                    |
| `Storyboard_Generation_Module`      | Builds wireframes and visual storyboards from scripts.                                    |
| `Videography_Direction_Module`      | Provides cinematographic guidance for presenters and media teams.                         |
| `Learning_Theories_Checklist_Module`| Performs QA checks on pedagogical completeness.                                           |
| `Instructional_Segment_Mapper`      | Maps segments to structure, role, theory tags, and scaffolding levels.                    |
| `Learning_Activity_Generator_Module`| Generates scaffolded activities aligned to objectives and audience level.                 |
| `Theory_Enhancement_Library`        | Supplies contextual academic theory snippets and citations.                               |

---

## 🔁 Orchestration & Usage

Modules are designed to be composable in prompt workflows using:

```python
include_module("Module_Name")
```

A full orchestration example might involve:

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

- Modules are locked on registration (`🔒`) and updated through version control.
- This repository supports instructional design teams, AI prompt engineers, and modular orchestration toolchains.
- Extendable via controller logic or metadata frameworks.

---

## 🛠 Contributing

To add a new module, submit a markdown spec following the existing format with:

- A unique name
- A version number
- A clear primary function and return schema

---

## 📄 Licence

This project is open for educational, non-commercial modular use. Contact the maintainer for integration or custom orchestration support.

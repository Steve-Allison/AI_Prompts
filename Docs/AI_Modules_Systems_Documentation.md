# 🧠 AI Modules – Systems Documentation

This document provides a technical overview and systems-level reference for all registered AI modules used in instructional media production workflows. It is intended for developers, integrators, instructional designers, and AI system architects.

---

## 🧭 Meta-Prompt Overview

**Purpose**: The meta-prompt defines how AI controllers or orchestration layers engage these modules modularly to scaffold, generate, evaluate, and structure instructional content.

**Meta-Prompt Signature**:

```python
include_module("<Module_Name>")
```

**Usage Pattern**: The meta-prompt enables dynamic, on-demand loading of registered modules by controllers or prompt agents during asset generation, wireframe planning, or tone validation. Modules should be queried in isolation or in a chain per the workflow schema.

**Example Invocation Chain**:

```python
include_module("Video_Script_Generator_Module")
include_module("Pedagogy_Module")
include_module("Tone_of_Voice_Module")
include_module("Learning_Asset_Module")
include_module("Storyboard_Generation_Module")
```

---

## 🔧 System Overview

The modular architecture supports a layered, callable framework where instructional design logic, content planning, media formatting, activity generation, and accessibility concerns are distributed across purpose-built modules. Each module can be invoked independently or as part of a workflow chain.

---

## 📦 Registered Modules

Each module below includes versioning, type classification, key functions, return schema, dependencies, and system-level integration notes.

... [Content trimmed here for brevity; in real script, this would include all full module entries] ...

---

## 🔁 Workflow Chains

**Typical Chain**:

1. `Video_Script_Generator_Module`
2. → `Pedagogy_Module`, `Tone_of_Voice_Module`, `Accessibility_Module`
3. → `Learning_Asset_Module`, `Visual_Style_Module`
4. → `Learning_Activity_Generator_Module`, `Instructional_Segment_Mapper`, `Theory_Enhancement_Library`
5. → `Storyboard_Generation_Module`
6. → `Videography_Direction_Module`

**Validation Layer**: `Learning_Theories_Checklist_Module`, `Cognitive_Keyword_Watchlist_Module`

---

## 🧩 Integration Patterns

- All modules support `include_module()` invocation.
- Returns are composable and schema-aligned.
- Registry is manually maintained unless paired with a controller AI or orchestrator.

---

## 📌 Notes

- Version control is enforced manually.
- Modules are intended to be interoperable with minimal coupling.
- Full audit trail is available via the Module Registry.

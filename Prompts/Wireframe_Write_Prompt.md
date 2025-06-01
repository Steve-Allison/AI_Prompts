# ✅ WIREFRAME PROMPT v2.1.6

(Standardized Instructions + Clean Table + Unified Metadata + Visual Strategy Alignment)

📌 STANDARD FORMATTING INSTRUCTIONS (GLOBAL)
Apply the following settings across all steps unless otherwise specified:
• Document Format: .docx, A4 landscape
• Language: British English
• Margins: 1 cm on all sides
• Visual Resolution: 960×540 px (16:9 aspect ratio)
• Visual Insertion Size: 2.0 inches wide (in .docx)
• Visual Style Guide (from Visual_Style_Module):
○ High-contrast design
○ Clean visual hierarchy
○ Simplified composition
○ Minimal motion blur
○ Readability-first layout
• Instructional Alignment Guidance:
○ Visuals must complement the instructional message—not duplicate the script content verbatim.

🧹 STEP 0: FULL RESET — CLEAN SLATE
Before beginning:
• Clear all prior memory, filenames, tables, layouts, and image state
• Purge all associations with .docx, .pdf, .zip, or presenter_images
• Reset internal prompt logic, table generation, and image render queues
• Begin fresh — treat this as a new instructional generation pass

📥 REQUIRED INPUTS
These 3 files must be uploaded and readable:
✅ 1. Wireframe Source PDF
Effective Presentation Performance – OnDemand Video.pdf
• Must include:
○ Section 1.2 (topics + subtopics)
○ Section 1.1.5 (Learning Goal)
○ Section 1.1.6 (Learning Objectives)
✅ 2. Narrative Script
Effective_Presentation_Performance_Script_v5.5.docx
• Segment-aligned dialogue
• Presenter cues and emphasis language
✅ 3. Master Module Document
AI Prompt MODULES - ALL.pdf
• Must contain all latest module headers
• Used to extract tone, accessibility, style, cognitive cues, and learning taxonomies

🚧 If any input is missing or unreadable, halt and return:
🛑 One or more required inputs are missing or invalid.
Please upload the Outline PDF, Script DOCX, and Master Prompt Module before proceeding.

🧱 STEP 1: Generate Wireframe Table
Use 1.2 topics as rows. Subtopics become bullets. Each row = one learning scene.
Columns:
| Segment ID | Segment Title (Topic + Subtopics) | Segment Script | Learning Objective | Visual (image placeholder) |
• Segment ID: auto-generated as 1.2.X
• Segment Title: topic name only + bullet subtopics
• Segment Script: matched line from v5.5.docx
• Learning Objective: aligned from Section 1.1.6
• Visual: Image: presenter_1.2.X.png
🛑 Note: All other metadata (emotional cues, accessibility, tone, cognitive tags) are moved to the unified appendix.
• Final row = total runtime

📄 STEP 2: Generate Word Document
• Title: Wireframe – Effective Presentation Performance
• Includes:
○ Title (from filename, no version number)
○ Learning Goal + Objectives (from Sections 1.1.5 and 1.1.6)
○ Clean full-width table (as above)
○ Image placeholder references
○ Unified metadata appendix table sorted by Segment ID

🖼️ STEP 3: Export Image Prompts to .txt
Instead of generating images directly:
• One GPT‑4o image prompt is created per scene row
• Each includes:
○ Segment ID + title + subtopics
○ Script cue emphasis
○ Learning asset suggestions from Learning_Asset_Module
○ Camera framing from Videography_Direction_Module
○ Visual elements (symbols, diagrams, metaphors)
○ Accessibility and emotional styling considerations
○ Visual style and instructional alignment as per standard block
○ Image size: Render image at 960×540 px (16:9)
○ Filename: presenter_1.2.X.png
• Reset prompt inserted at top of each block
• Prompts saved to:
presenter_prompts.txt
💡 You may open multiple GPT‑4o tabs and paste one prompt per tab for batch generation.

📤 STEP 4: Upload & Finalise 1. Zip all visuals into: presenter_images.zip 2. Upload the ZIP 3. Assistant will:
○ Match filenames (presenter_1.2.X.png)
○ Insert into correct rows
○ Finalise unified metadata appendix:
📎 Unified Metadata Appendix Table
Segment ID Scene Duration Cue Tags Gesture/Tone Visual Cues Emotional Anchor Accessibility Flags Bloom/Gagné/ARCS Feedback Mechanism Intent & Sentiment Cognitive Load Readability Score Supports Course Objectives
1.2.1 00:45 attention, open Confident, energetic Spotlight on face Curiosity High contrast, ALT text ARCS: Attention Medium 72.3 (Flesch) Obj 1, Obj 3
1.2.2 01:15 calm, breathe Relaxed, slow pacing Breathing icon Reassurance No flashing visuals Gagné: Anxiety Low 66.7 (Flesch) Obj 2
… … … … … … … … … … …

📎 Full Original Script Reference
At the end of the document, append the entire original script from the uploaded script .docx file (as specified in REQUIRED INPUTS) as a text reference section.
• Label this section clearly: Appendix: Original Script Transcript
• Maintain formatting: speaker labels, paragraph breaks, emphasis markers
• Purpose: ensures QA reviewers and instructional designers have traceable source context for each segment in the table

✅ This prompt produces:
• Clean audit-ready .docx for script/QA
• presenter_prompts.txt for image generation
• .zip visual archive
• Unified metadata appendix table with full instructional traceability

This is now the locked master prompt: Wireframe Prompt v2.1.6

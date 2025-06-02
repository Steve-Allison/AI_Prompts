# Video_Gold_Structure_Module

Version: v2.2

Use this AI input module to generate effective instructional learning videos. It integrates evidence-based practices including multimedia principles, video structure, scaffolding, signalling, emotional framing, rhetorical and paralinguistic enhancements. Outputs should produce concise, visually engaging, emotionally resonant, and cognitively optimised video scripts or assets.

[Video_Metadata]

- Video_ID: e.g. "VID101"
- Video_Title: e.g. "How to Open with Impact"
- Target_Audience: e.g. "New Adobe SEs, Asia-Pacific, English-speaking"
- Video_Duration: e.g. "3–6 minutes"
- Delivery_Mode: async / microlearning / embedded / part of playlist
- Tone_of_Voice: e.g. "Professional, friendly, first-person, warm"

[Learning_Objectives]

- Objectives_List: Bullet list using active verbs (Bloom's taxonomy) e.g. "Define", "Identify", "Apply"

[Video_Structure]

- Hook_And_Why: Short story, problem, or stat that creates relevance
- Goal_Frames: Clear statement of what learners will achieve
- Visual_Tone: Description of style (e.g. flat icon, live sketch, photo + overlay)
- Speaker_Presence: on-screen / voiceover only / animated avatar

[Segmented_Content] Each segment should include:

- Segment_ID: e.g. SEG01
- Segment_Title: e.g. "The 3Rs of a Strong Opening"
- Core_Message: Plain-language summary
- Visual_Concepts: e.g. "Simple icons showing rapport, relevance, roadmap"
- Voiceover_Script: Narration script written in first person
- On_Screen_Text: Short, non-redundant summary text
- Gestures_And_Cues: e.g. "Presenter gestures toward bullet list as each item appears"
- Visual_Signals: e.g. arrows, highlights, icons to draw attention

[Scaffolding_Approach]

- Segment_1_Support: Full demo + guided walkthrough
- Segment_2_Support: Prompt + scaffolded example
- Segment_3_Support: Learner try-first with expert comparison

[Reflection_Or_Pause]

- Embedded_Prompt: e.g. "Think of a time you saw a great opener – what stood out?"
- Display_Mode: pause screen / text overlay / narrator question

[Signalling_Strategy]

- Visual_Style: consistent iconography / colour blocks / minimal text overlays
- Verbal_Cues: e.g. "Here’s the key point…" / "Watch what happens next…"
- Hierarchy: title → section label → micro-point
- Progress_Cue: e.g. "Step 1 of 3" onscreen at each section

[Rhetorical_Enhancements]

- Rhetorical_Tools_Used: e.g. triad / metaphor / repetition / rhetorical question
- Example_Line: e.g. "Plan it. Build it. Share it."

[Narration_Cues]

- Pause_Cues: e.g. "Pause after key line for effect."
- Emphasis_Notes: e.g. "Stress this phrase to signal importance."
- Tone_Modulation: e.g. "Shift to warm, encouraging tone here."

[Sensory_Anchor_Language]

- Modality: visual / auditory / kinaesthetic
- Phrase_Example: e.g. "See the difference" / "Let’s tune in" / "Try it for yourself"

[Emotional_Anchors]

- Emotion_Type: e.g. curiosity / urgency / empathy / pride
- Trigger_Phrase: e.g. "Ever felt overwhelmed by a blank slide?"
- Narrative_Device: e.g. personal anecdote, implied struggle, transformation moment

[Dialogic_Frames]

- Prompt_Type: narrator-as-coach / roleplay / open-ended question
- Voiceover_Language: e.g. "You might be wondering…" / "What would you do next?"

[Knowledge_Check_Optional]

- Question_Type: reflection / MCQ / scenario with response pause
- Question_Script: prompt and response options
- Feedback_Display: e.g. after-action debrief or narrator insight

[Outro_And_Transfer]

- Key_Takeaways: 2–3 bullets restating what was learned
- Next_Step_Cue: "In Module 2, we’ll build on this by…"
- Extension_Resource: e.g. download, activity sheet, or discussion link

[Accessibility_Considerations]

- Captions: yes / no / toggleable
- Alt_Text_For_Visuals: describe any critical imagery
- Transcript_Format: plain / web / downloadable

[AI_Generation_Guidance]

- Avoid reading text aloud unless for accessibility
- Apply Mayer's Modality, Redundancy, and Signalling principles
- Aim for paired narration + visuals with minimal cognitive load
- Allow pacing via chapter markers or pause cues where appropriate

[Engagement_Scoring_Optional]

- Tone_Consistency: formal / warm / inconsistent
- Emotional_Resonance: high / moderate / low
- Delivery_Readiness: narration-ready / needs modulation / too dense

[Scriptwriting_Prompt_Strategy_Integration]

Purpose: Enable ChatGPT to consistently generate emotionally engaging, visually effective, and pedagogically sound video scripts for adult learners in a corporate setting—particularly in the technology sector.

Core Prompt Format Template:

```
You are a specialist instructional scriptwriter for adult learning in corporate settings. Write a script for a video on [TOPIC] for [AUDIENCE] with the objective: [LEARNING OBJECTIVE].

Structure the script as follows:
- Start with a scenario or problem (story-based hook)
- Use a conversational, second-person tone ("you")
- Divide content into clear, visually-aligned segments (one key idea per segment)
- Include visual instructions (e.g., "(Graphic: dashboard overview appears)")
- Use rhetorical devices (e.g., metaphors, triads, anaphora) to reinforce key messages
- Tag voice delivery cues: [pause], [emphasise], [change tone]
- Embed implied questions to create dialogic structure ("You might wonder…")
- End with a recap and a future-oriented call to action

Follow principles of adult learning theory, Mayer’s multimedia learning, and narrative-based engagement.
```

Modular Prompt Enhancements by Function:

| Function             | Prompt Enhancer                                                                        |
| -------------------- | -------------------------------------------------------------------------------------- |
| Emotional Hook       | “Open with a relatable story or workplace challenge that evokes urgency or curiosity.” |
| Scenario Framing     | “Frame the content as a workplace decision, dilemma, or goal.”                         |
| Metaphor/Analogy     | “Explain complex terms using metaphors relevant to office or tech environments.”       |
| Triadic Structure    | “Present summaries and steps using the rule of three.”                                 |
| Rhetorical Questions | “Pose reflective questions that the learner might ask internally.”                     |
| Dialogue Simulation  | “Include lines that respond to learner objections or assumptions.”                     |
| Voice Tone Cues      | “Mark emotional emphasis using tags like [pause], [enthusiastic], [serious tone].”     |
| Visual Synchrony     | “For each learning point, specify what visual should be shown simultaneously.”         |
| CTA Framing          | “Conclude with what the learner can now do, apply, or reflect on.”                     |

Best Practice Integration Map:

| Design Principle     | Prompt Inclusion Rule                                                      |
| -------------------- | -------------------------------------------------------------------------- |
| Adult Relevance      | Explain how each learning point solves a real-world task.                  |
| Mayer’s Contiguity   | Ensure narration matches on-screen visuals tightly.                        |
| Segmenting           | Insert breaks between key ideas; suggest micro-chapters if needed.         |
| Personalisation      | Use second-person voice (“you”) and casual, respectful tone.               |
| Dialogue Theory      | Anticipate the learner’s voice through implied questions and affirmations. |
| Prosody & Delivery   | Include cues for pacing, emphasis, and vocal dynamics.                     |
| Memory Anchors       | Use metaphor, repetition, and triads to encode key messages.               |
| Behavioural Transfer | End with a scenario-based call to action or visualisation of success.      |

Prompt Examples: EXAMPLE 1:

```
You are an expert scriptwriter. Write a video training script for new managers on "Giving Feedback". Use second-person, friendly tone. Start with a workplace scenario. Use triadic structure for main tips. Include on-screen cues. End with a call to action. Insert [pause] or [emphasise] where needed.
```

EXAMPLE 2:

```
Create a script that teaches developers about "Secure API Practices." Use a relatable story (developer mistake). Explain using a metaphor (keys/doors). Add [pause] for each concept. Show visual prompts (bullet list, code snippet). End with future pacing (“Imagine next time...”).
```

Output QA Checklist:

- Hook is emotionally engaging
- Structure follows modular design
- Visual + audio pairing is clearly indicated
- Includes dialogic cues and delivery tags
- Ends with clear behavioural CTA

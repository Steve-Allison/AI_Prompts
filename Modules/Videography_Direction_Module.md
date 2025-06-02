# Videography_Direction_Module

**Version:** 2.1

Provides structured, best-practice cinematography guidance for learning videos. Designed for use by AI prompt chains that generate or analyse educational video content.

---

### Expected Inputs from Calling Prompt

```
{{video_title}}           - String: the video's title
{{learning_goal}}         - One sentence description of the intended learner outcome
{{learning_objectives}}   - List of 2–4 instructional objectives
{{script}}                - Full instructional script (text only)
{{visual_style}}          - Tone descriptor (e.g., "professional and passionate")
{{delivery_markers}}      - (Optional) List of markers or gestures from Tone_of_Voice_Module
```

---

## Embedded Sub-Modules

---

### MODULE: Visual Style Compliance (from visual_style_module)

Use `visual_style_module` values (if available) to align all visual direction with approved branding and accessibility standards:

* **Typography**: Ensure overlay text follows the approved font, size, line height, and contrast requirements.
* **Colour Palette**: Use specified brand colours; maintain contrast for accessibility (check contrast ratios).
* **Layout & Geometry**: Ensure screen elements (e.g., graphics or callouts) use approved layout guides and shape language.
* **Image Treatment**: Only use transparent PNGs or clean-cropped photos; maintain consistency in presenter framing.
* **Animation Potential**: Flag where animated transitions or visual metaphors are allowed by visual brand rules.

---

---

### MODULE: Cognitive Cue Integration

Use cognitive/emotional cue tags from the script (e.g., `[confidence_anchor]`, `[reflective_pause]`, `[curiosity_peak]`) to inform framing, shot changes, and pacing.

| Cue Tag               | Camera & Visual Direction                                               |
| --------------------- | ----------------------------------------------------------------------- |
| \[confidence_anchor] | Mid-close shot, direct eyeline, strong frontal lighting                 |
| \[reflective_pause]  | Slow zoom-in or fade to close-up, softened background                   |
| \[curiosity_peak]    | Dynamic angle change or visual pop-up (e.g., icon or emoji-like marker) |

If cue tags are missing but can be inferred from rhetorical shape or pacing, generate appropriate camera emphasis based on tone and learning goal.

---

---

### MODULE: Visual Learning Principles

(Cognitive + visual best practices from Mayer, Vimeo/Wistia, and instructional design)

* Alternate medium and close-up shots every 8–15 seconds or at natural breakpoints
* Frame using rule of thirds, eye-level, consistent headroom
* Cut on gestures, transitions, and rhetorical cues
* Use green screen to layer simple, supportive backdrops (slides, diagrams, metaphors)
* Support narration with keywords, icons, and signalled emphasis
* Segment into visual chapters, reinforce with mini-recaps

---

### MODULE: Visual Style Alignment (from Tone Profile and Learning Theory Alignment)

In addition to visual tone from `{{visual_style}}`, adjust direction using instructional intent tags such as `[Bloom: Apply]`, `[ARCS: Attention]`, `[Gagné: Elicit Performance]`.

| Instructional Tag            | Visual Adjustment                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------- |
| \[Bloom: Apply]              | Close-up framing, encourage gesture emphasis                                           |
| \[ARCS: Attention]           | Quick cut, bold visual animation or camera movement                                    |
| \[Gagné: Elicit Performance] | Mid shot showing full arm gestures, often with whiteboard or visual prop in background |

Align these with tone and persona. Override gently if there's tonal conflict (e.g. calm style with \[ARCS: Attention] tag).

Align visual and staging tone with the provided {{visual_style}}:

| Visual Style              | Framing                   | Rhythm & Cuts                     | Background & Lighting             |
| ------------------------- | ------------------------- | --------------------------------- | --------------------------------- |
| Professional & Passionate | Mid/close-up; steady      | Cuts on beat, gestures, shifts    | Soft key light; clean gradient    |
| Calm & Supportive         | Medium-wide, static       | Slow fade/cuts every 15–20 sec    | Muted palette, soft edges         |
| Bold & Motivational       | Tight close-ups, tracking | Fast cuts; emphasise transitions  | Strong key/fill, vibrant backdrop |
| Trusted with Wit          | Mid with headroom         | Playful rhythm, rhetorical pauses | Balanced light; minimal props     |

You may override with a persona-specific tone (e.g., "Steve Allison – trusted, energetic guide with subtle wit") to fine-tune gestures and cut timing.

---

### MODULE: Visual Staging Integration (from Delivery Markers)

If {{delivery_markers}} are provided (or inferred), apply this framing and emphasis:

| Marker                | Recommended Shot        | Camera Action             | Lighting Note              |
| --------------------- | ----------------------- | ------------------------- | -------------------------- |
| \[gesture: open arms] | Wide shot               | Static                    | Warm, even lighting        |
| \[step forward]       | Mid-close; slow push-in | Track forward or zoom-in  | Increased key light        |
| \[lower tone]         | Tight close-up          | Static or slight dolly-in | Dimmed contrast lighting   |
| \[pitch lift]         | Head-tilted close-up    | Side camera cut or zoom   | Boost fill, highlight face |

Synchronise camera emphasis within 0.5s of the gesture onset (or pitch inflection). Match movement to performance intent.

---

### MODULE: Character Staging Integration (from character_module)

If a `character_module` persona profile is present (e.g., "Steve – British Business Presenter"), apply the following for visual and stage planning:

* **Framing defaults**: Match preferred posture and eye contact with medium or mid-close shot framing.
* **Movement habits**: Use `[step forward]` or lateral stage shifts to cue segment transitions or emphasis.
* **Clothing/contrast**: Ensure wardrobe colours are distinct from green screen or background overlays.
* **Gesture palette**: Use subtle, expressive gestures that match the persona's behavioural cues.

---

### MODULE: Learning Asset Cue Detection (from learning_asset_module)

Where cue tags or learning objectives suggest asset opportunities, visually reinforce or flag with the following:

* **Reflection cues** (e.g. "pause and consider..."): Insert on-screen banners or motion overlays.
* **Diagram triggers** (e.g. triad lists, processes): Suggest simple animated diagrams or static slides.
* **Practice or challenge** statements: Indicate callout overlays, lower-thirds, or background changes.

These are handed off to `learning_asset_module` if available.

---

### MODULE: Accessibility Annotations

When delivery markers (e.g. `[gesture: open arms]`, `[step forward]`) are used, provide accessibility equivalents:

| Marker                | Captioning Note                  | Audio-Only Alternative                |
| --------------------- | -------------------------------- | ------------------------------------- |
| \[gesture: open arms] | \[visual: arms extended outward] | "This includes all of us."            |
| \[step forward]       | \[visual: step toward camera]    | "Let's move into the next part."      |
| \[lower tone]         | \[audible drop in tone]          | "Let's reflect on this for a moment..." |

Include these in `Speaker Delivery Notes` if script is intended for captioning, TTS, or audio-first playback.

---

### MODULE TASK: Generate Visual Direction

For each logical section or paragraph of the {{script}}, generate:

1. Primary Camera Framing – Shot type, eyeline, headroom, posture
2. Second Camera Angle – Variation and rhythm; where to cut
3. Shot Transitions & Rhythm – When/why to cut, transitions, gesture syncing
4. Green Screen Background – Suggested use: clean, context-matching, instructional
5. On-screen Graphics & Text – Visual emphasis: keywords, icons, diagrams, callouts
6. Speaker Delivery Notes – Gesture, emphasis, pacing, tone (based on {{visual_style}} or delivery persona)

---

### OUTPUT FORMAT

Repeat for each section of the script:

```
### Section [X]: "[Opening phrase or summary of this segment]"

- Primary Camera Framing: ...
- Second Camera Angle: ...
- Shot Transitions & Rhythm: ...
- Green Screen Background: ...
- On-screen Graphics & Text: ...
- Speaker Delivery Notes: ...
```

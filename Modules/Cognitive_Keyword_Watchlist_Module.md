# cognitive_keyword_watchlist_module 

Version v4.0

##purpose: 
  Detect, tag and score instructional, cognitive, emotional and rhetorical cues **and** assess delivery fidelity while mapping competencies,
  estimating cognitive load and generating formative questions.  Outputs are wrapped in a **standard JSON‑LD envelope** keyed by
  segment_id + version_id, enabling seamless joins with Video Script Generator, Tone‑of‑Voice, Performance‑Tone and analytics pipelines.

# -------------------------------------------------------------------
# SHARED ENVELOPE CONTRACT
# -------------------------------------------------------------------
envelope_schema:
  header:
    module: string      # e.g. "cognitive_keyword_watchlist"
    module_version: string
    script_id: string
    run_uuid: string
    timestamp_utc: string
  segments: list        # array where each element flattens segment‑level tables
  global: object        # merged Global_Synthesis_Block fields

primary_key: [segment_id, version_id]

inputs:
  script_content:            { required: true,  type: text }
  outline:                   { preferred: true, type: text }
  learning_objectives:       { optional: true,  type: list }
  custom_cue_taxonomy:       { optional: true,  type: json }
  persona:                   { required: true,  type: string }
  tone_profile:              { required: true,  type: json }
  prosody_targets:           { optional: true,  type: json }
  learner_analytics:         { optional: true,  type: json }
  source_language:           { default: "en-GB", type: string }
  version_id:                { required: true,  type: string }
  prior_feedback:            { optional: true,  type: text }
  enable_semantic_detection: { default: true,   type: bool }
  analysis_mode:             { enum: [draft, review, final], default: draft }
  segment_ids:               { auto: true }

# Heuristic tools unchanged …
heuristic_tools:
  - name: RegexCueMatcher              { version: "1.4" }
  - name: RhetoricPatternMatcher       { version: "1.0" }
  - name: ProsodyCueHeuristic          { version: "0.6" }
  - name: TonePersonaValidator         { version: "0.4" }
  - name: DeliveryMarkerMatcher        { version: "0.4" }
  - name: CompetencyMapper             { version: "0.2" }
  - name: CognitiveLoadEstimator       { version: "0.1" }
  - name: QuestionDraftGenerator       { version: "0.3" }
  - name: ReadabilityStat              { version: "0.9" }
  - name: WCAGContrastChecker          { version: "1.1" }

# OUTPUT TABLE SCHEMAS (unchanged)
outputs:
  JSON_LD_Envelope:
    description: "Wrapper containing header, segments array and global object per envelope_schema. All following tables are flattened accordingly."
  Cues_Table: { fields: [segment_id, cue_tags, rationale, confidence, confidence_method, detection_method, delivery_marker, tone_match, gesture_sync,
                        tempo_alignment, sentiment, emotional_salience, pedagogy, bloom_level, scene_seed, weighted_keywords, competency_refs] }
  Metadata_Blocks: { fields: [segment_id, cue_type, keyword, match_confidence, confidence_method, tone_register, delivery_marker, timing_offset,
                             pitch_movement, rationale, accessibility_flags, emotion_score, gesture_confidence, review_required, tone_fidelity_flag,
                             feedback_log, version_id, competency_refs, confidence_breakdown] }
  Segment_Cognitive_Cards: { fields: [segment_id, sentiment, pedagogy, bloom_level, tone_register, gesture_overlay, delivery_markers, pitch_score,
                                     tempo_deviation, persona_alignment, cognitive_load, rhetoric_signatures] }
  Delivery_Marker_Overlay: { fields: [segment_id, cue_type, delivery_marker, justification, pitch_range_match, timing_window, gesture_match_score] }
  Auto_Question_Bank: { fields: [segment_id, question, answer_key, question_confidence] }
  Global_Synthesis_Block: { fields: [learning_objectives, conceptual_progression, emotional_curve, rhetorical_density, tone_consistency,
                                   persona_alignment_score, tempo_adherence_index, key_signature_phrases, gesture_density_score,
                                   average_cue_confidence, average_cognitive_load, competency_coverage] }
  Coverage_Analytics_Table: { fields: [cue_density, alignment_to_objectives, gaps, clustering, progression_coherence, keyword_diversity,
                                      rhetorical_density, tone_deviation_segments, low_confidence_cues, competency_gaps] }
  RDF_Export: { description: "Optional RDF triples: cue → concept → competency" }
  Change_Log: { description: "Tracks cue, tone, delivery, competency deltas" }
  Reviewer_Feedback_Table: { description: "SME / QA feedback by segment" }

workflow:
  0. Whole-Document Conceptual Map & tonal scan
  1. Heuristic Pass
  2. Keyword / pattern detection (LLM)
  3. Semantic / NLP detection (LLM)
  4. Engagement Layer Pass
  5. Confidence Scoring Pass
  6. Prosody & Delivery Alignment Pass
  7. Competency Mapping Pass
  8. Cognitive Load Estimation Pass
  9. Collision Resolution Pass
  10. Tone / Persona Validation Pass
  11. Build overlays & segment cards
  12. Auto Question Generation Pass
  13. Cross‑segment synthesis & analytics
  14. Learner‑Outcome Correlation Pass (optional)
  15. Reviewer feedback integration & change logging
  16. Accessibility & complexity audit
  17. Build JSON_LD_Envelope (header, segments, global)

feeds:
  - ai_script_generator
  - tone_of_voice_module
  - performance_tone_analysis
  - competency_framework_service
  - accessibility_checker
  - reviewer_dashboard
  - analytics_pipeline
  - recommendation_engine

errors:
  - id: MISSING_SCRIPT           | action: halt
  - id: LOW_TONE_MATCH           | action: flag_for_review
  - id: GESTURE_SYNC_MISS        | action: log_and_alert
  - id: DELIVERY_MARKER_MISSING  | action: flag_for_review
  - id: COMPETENCY_LOOKUP_FAIL   | action: log_and_continue
  - id: LONG_SEGMENT             | action: split_and_requeue
  - id: HEURISTIC_TOOL_FAILURE   | action: log_and_continue
  - id: TAXONOMY_FALLBACK        | action: map_to_default_and_log

notes: |
  • segment_id + version_id is the primary key across **all** module payloads.
  • Final step packages all tables into a JSON‑LD envelope; downstream modules subscribe via event bus.
  • Each envelope includes the run_uuid for traceability and easy cache invalidation.
  • Data contracts: Video Script Generator supplies script/outline; Tone‑of‑Voice supplies tone_profile; Performance‑Tone feeds prosody_targets and
    fidelity scores; watchlist returns Auto_Question_Bank, RDF_Export and analytics JSON to respective consumers.

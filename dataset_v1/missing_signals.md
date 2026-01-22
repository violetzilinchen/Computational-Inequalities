# missing_signals.md
## Reflecting on what the system fails to record (Children’s animation recommendation harms)

This note reflects on the *missing* or *unseen* signals in platform metadata that prevent harms from being recognised, measured, and governed. In my dataset of children’s animation content circulated via algorithmic feeds/autoplay, the platform’s “success” signals (e.g., views, watch time) are highly legible, while signals of age-inappropriateness, manipulation, and child wellbeing impacts remain largely invisible.

---

## Q1. What can you observe, but the system’s metadata does not contain?

### 1) Visual cues of age-inappropriateness are not recorded
I can observe recurring visual elements that indicate potential harm (e.g., threat/terror framing, chasing, punishment scenes, aggressive gestures, weapons as props, sudden jump-scares, dark atmospheres). However, standard metadata typically captures *titles/tags, thumbnails, and engagement counts* rather than structured fields that encode *what actually happens on-screen*.

### 2) Audio intensity and “shock” signals are absent
Many videos rely on loud peaks, high-frequency effects, screams, and dense sound-effects to hold attention. These audio patterns are salient to children’s arousal and distress but are not represented in metadata (no fields for loudness peaks, scream-event density, or audio harshness).

### 3) Autoplay chains and “looping” exposure are not legible as risk
I can observe serialised chains (Part 1/2/3, compilations, loops) and template repetition that produce prolonged sessions and difficulty stopping. The system may log *per-video* performance but rarely exposes structured information about *cross-video chaining*, *autoplay depth*, or *template similarity* as potential risk signals.

### 4) Caregiver concerns are weakly represented or unstructured
Where negative feedback exists (comments, reports, external discussion), it is typically not captured as interpretable categories (e.g., “my child was scared”, “too loud”, “addictive/looping”, “misleading educational label”). Instead, the platform foregrounds aggregate engagement counts, which can mask harm.

---

## Q2. Which harms / meanings are not captured by the system?

### 1) Psychological harm and age–content mismatch
Harms such as fear, anxiety, nightmares, or distress are experiential and developmental. They do not map neatly onto engagement metrics, and therefore are systematically under-captured.

### 2) “Benefit-washing” / misleading framing (pseudo-educational claims)
A key distortion is when content is labelled as “educational”, “kids safe”, or “learning ABC/123/colours”, while the actual content provides little structured learning and instead optimises for retention through repetition and stimulation. The system may treat these labels as positive relevance signals, amplifying mislabelled content.

### 3) Attention capture through overstimulation
High saturation, rapid cuts, flashing, and intense audio can maximise engagement while potentially undermining children’s regulation, rest, and attention. Such harms are not visible to systems that primarily optimise for watch time and clicks.

### 4) Commercial manipulation disguised as entertainment
Unboxing, toy showcases, and stealth advertising blur the boundary between play and marketing. Without explicit commercial-intent signals, the system cannot reliably distinguish entertainment from persuasion targeted at children.

---

## Q3. How should we change data recording so these harms become “visible”?

To enable targeted intervention, the dataset/metadata should be expanded beyond engagement and text labels to include *multi-modal risk signals* and *structured human feedback*. Below are practical fields that could be recorded via a combination of rule-based extraction and AI-assisted analysis:

### 1) A structured risk taxonomy field
- **Proposed fields:** `risk_theme` (e.g., fear, violence/punishment, dark-scenes, sexualised cues, commercial persuasion, misinformation/misleading claims)
- **Why it matters:** makes harms governable by allowing ranking, down-weighting, age-gating, and auditing by harm type rather than relying on vague “inappropriate” flags.

### 2) Multi-modal content cues (vision + audio)
- **Proposed fields:**  
  - `visual_risk_cues` (threat/chase, aggression gestures, jump-scare frames, weapon props, crying/terror facial expressions, darkness ratio)  
  - `audio_intensity_metrics` (peak loudness, scream-event density, high-frequency harshness, sound-effect density)
- **Why it matters:** reduces over-reliance on text tags and thumbnails, which are easily manipulated.

### 3) Label–content mismatch indicators
- **Proposed fields:** `claim_tags` (educational/kids-safe claims), `content_structure_score` (presence of pedagogical structure: explanation, examples, repetition with feedback), `mislabel_risk` (boolean)
- **Why it matters:** identifies “educational” claims that function as distribution hacks rather than genuine pedagogy.

### 4) Looping and exposure-chain measures
- **Proposed fields:** `series_chain_id`, `autoplay_depth`, `template_similarity_score`, `session_risk_flag` (for unusually long sessions in child contexts)
- **Why it matters:** treats *exposure patterns* (not just single videos) as a site of harm.

### 5) Structured caregiver feedback signals
- **Proposed fields:** `parent_complaint_flag`, `negative_feedback_type` (scary/too loud/addictive/misleading/ad-like), `complaint_intensity`
- **Why it matters:** integrates lived experience and care-based concerns into governance, aligning the system with equity and child wellbeing rather than only engagement.

---

## Summary
Current platform metadata privileges what is easy to quantify (views, watch time, likes) and under-represents what is ethically and socially consequential (age-appropriateness, distress signals, overstimulation, commercial manipulation, and caregiver concern). Making these signals explicit—through a risk taxonomy, multi-modal detection, mismatch indicators, chain-level exposure metrics, and structured feedback—would enable more equitable and accountable interventions in children’s animation recommendation systems.

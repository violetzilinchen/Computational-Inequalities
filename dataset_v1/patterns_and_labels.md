---

## Label 1: [Cute-bait Inappropriate Content]
- Harm / framing / pattern:
  - Uses “kids/learning/nursery rhymes/educational” keywords and familiar children’s IP (e.g., Elsa/Spiderman/Peppa) plus bright, child-friendly thumbnails to attract clicks, while the actual video contains fear, threat, punishment, chasing, mild violence, or dark/creepy scenes.
  - Produces age–content mismatch and potential psychological distress (fear, nightmares, anxiety) while remaining “legible” as children’s content to the recommender.
- What the system must detect:
  - Text: co-occurrence of kid-safe/learning claims (“learn”, “nursery rhymes”, “kids”, “baby”, “kids safe”, “educational”) + character/IP terms.
  - Vision: child-friendly thumbnail style but keyframes contain threat cues (chasing, weapons/props, aggressive gestures, crying/terror facial expressions, darkness ratio, jump-scare frames).
  - Audio: scream events, sudden loud peaks, horror-like music cues.
  - Rule: if “kid-friendly claims” AND “fear/violence cues” are both present → down-rank, age-gate, or route to human review.

---

## Label 2: [Mislabelled “Educational / Kids-safe” Content]
- Harm / framing / pattern:
  - Claims to be “educational”, “learning ABC/123/colours”, or “kids safe”, but provides little pedagogical structure or learning value; instead optimises retention through repetition and stimulation (“benefit-washing” / label misuse).
  - Distorts parental trust and amplifies low-value content via metadata-based ranking.
- What the system must detect:
  - Text: education/learning claims (“educational”, “learn”, “ABC”, “123”, “phonics”, “colours”, “kids safe”).
  - Claim–content mismatch: does the video actually contain teaching structure (explanation, examples, guided practice, feedback), or only looping fragments?
  - A mismatch indicator: high “education claim score” + low “teaching structure score” → `mislabel_risk = true`.
  - Intervention: reduce recommendation weight and trigger review for repeated mislabelling.

---

## Label 3: [High-engagement, Low-value Looping (Autoplay Trap)]
- Harm / framing / pattern:
  - Achieves high engagement while offering minimal informational/narrative value by chaining “Part 1/2/3”, compilations, and template-repeated videos, encouraging long sessions and difficulty stopping.
  - Exposure-level harm: time loss, disrupted routines (especially near bedtime), and reduced autonomy in children’s media use.
- What the system must detect:
  - Exposure chain signals: `autoplay_depth`, session length, consecutive play count, repeat viewing rate.
  - Template repetition: high audio/visual similarity across videos; repeated intros/outros; repeated segments ratio.
  - Text markers: “Part 1/2/3”, “compilation”, “loop”, “24 hours”, “full episode/全集/合集”.
  - Rule: if high repetition + strong chain structure + child context/time-of-day → limit autoplay, down-rank chain, prompt breaks.

---

## Label 4: [Overstimulation / Attention Capture Design]
- Harm / framing / pattern:
  - Uses high saturation, rapid cuts, flashing, exaggerated facial expressions, and loud/sharp sound effects to maximise clicks and watch time.
  - Potential impacts include over-arousal, difficulty calming down, sleep disruption, and attention instability—harms that are not reflected in standard engagement metrics.
- What the system must detect:
  - Vision: cut rate (shots/min), flashing frames ratio, saturation/contrast outliers, motion intensity.
  - Audio: peak loudness, high-frequency harshness, sound-effect density, scream-event density.
  - Text: stimulation terms (e.g., “OMG”, “crazy”, “surprise”, “don’t watch”, “scary”).
  - Intervention: apply “stimulation thresholds” for child-targeted content; down-rank or add caregiver warnings when thresholds are exceeded.

---

## Label 5: [Stealth Advertising / Commercial Manipulation]
- Harm / framing / pattern:
  - Unboxing, toy showcases, branded props, and purchase prompts are embedded in entertainment, blurring the boundary between content and advertising for children.
  - This can drive consumption pressure and persuasive influence without clear disclosure.
- What the system must detect:
  - Vision: product close-ups, brand/logo detection, packaging/unboxing sequences, price/purchase cues.
  - Text: “unboxing”, “toy”, “new set”, “link”, “discount”, “buy”, “order”, “shop”.
  - Structure: pinned comments/description links, QR codes, explicit calls-to-action, repeated brand mentions.
  - Intervention: enforce clear ad labelling; reduce distribution in child contexts; review repeated undisclosed commercial content.

---
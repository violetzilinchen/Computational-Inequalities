# Taxonomy v2 Limitations Analysis
## 1. Where the Taxonomy Works
- **Clear binary classification of core categories**: The taxonomy effectively distinguishes between unambiguous "harmful" content (e.g., *ed35cd06-rickMorty_vindicators_compilation_04.png* with `Threat/Intimidation` labels) and "child-coded" content (e.g., *67859690-peppaPig_holidayAdventure_fullEpisodes_07.png*), providing clear guidance for system filtering or prioritization.
- **Reliable identification of explicit elements**: Labels like `Familiar-Character/IP` and `Packaging/Text` consistently capture visible, non-ambiguous features—all 10 images have accurate annotations for these categories, with no misclassification in the cleaned data.
- **Alignment with cleaning logic**: The taxonomy’s core labels (e.g., `Threat/Intimidation`, `Adult-Inappropriate`) map seamlessly to the cleaning script’s `MERGE_MAP`, enabling consistent aggregation into high-level labels like "harmful" for large-scale processing.

## 2. Where Meaning Is Forced or Collapses
- **Overwritten nuance in multi-label images**: Images with overlapping categories are forced into a single "image_level_label" during cleaning. For example:
  - *7db3d984-shinchan_new_episode_english_subtitles_03.png* has both `Adult-Inappropriate` (harmful) and `Familiar-Character/IP` labels, but the cleaned image-level label is `familiarcharacter_ip`—erasing the critical "adult-inappropriate" context.
  - *45ec4c7c-freddy_fnaf_animation_horror_01.png* includes both `Creepy-Setting` and `Threat/Intimidation`, yet is labeled `creepysetting` at the image level, minimizing the threat element.
- **Ambiguous scenes forced into rigid categories**: The taxonomy lacks middle-ground labels for "mildly unsettling" or "context-dependent risk" scenes. For example, *cc7f9860-snoopy_beagleScout_snoopyShow_appleTV_08.png* has an `Unclear/Needs-Context` region but is forced into `familiarcharacter_ip` at the image level, ignoring unresolved ambiguity.
- **Over-simplification of "harmful" content**: The cleaning script merges `Threat/Intimidation` and `Adult-Inappropriate` into a single "harmful" label, collapsing distinct harm types (psychological threat vs. age-inappropriate content) into one undifferentiated category.

## 3. What the System Still Cannot Express
- **Emotional and contextual cues**: The taxonomy fails to capture subjective but critical cues like character emotions (e.g., fear in child-coded characters) or narrative context. For example, *45ec4c7c-freddy_fnaf_animation_horror_01.png*’s oppressive composition conveys dread, but this emotional impact has no corresponding label.
- **Risk intensity gradients**: There is no mechanism to distinguish between mild and severe risk. A minor threat (e.g., a playful "scary" costume) and a severe threat (e.g., menacing posture with shadows) are both labeled `Threat/Intimidation` with no gradation.
- **Contextual dependency details**: The `Unclear/Needs-Context` label is vague and provides no specifics. For example, *9b191083-pokemon_evolution_animated_explained_05.png*’s `Unclear` region cannot express whether additional frames or episode context are needed to assess conflict or scariness.
- **Interactions between categories**: The system cannot express relational meaning, such as "child-coded characters exposed to harmful content"—it only labels each category separately, missing the critical interplay that defines risk for minors.

## 4. Which Distinctions Disappear at Scale
- **Loss of label granularity**: The cleaning script’s `MERGE_MAP` eliminates sub-category distinctions. At scale:
  - `Threat/Intimidation` and `Adult-Inappropriate` are both reduced to "harmful," making it impossible to tailor interventions (e.g., filtering adult content but allowing mild fantasy threats).
  - `Familiar-Character/IP` loses specificity (e.g., no distinction between child-friendly IP like Peppa Pig vs. mature IP like Rick and Morty).
- **Erasure of multi-label complexity**: Large-scale processing enforces a single label per image (via `image_level_label`), deleting evidence of mixed content. For example, images that blend child-coded visuals with harmful themes—critical for identifying "misleading child-centric content"—are reduced to one dominant label.
- **Disappearance of uncertainty**: The `Unclear/Needs-Context` label is simplified to "unclear" during cleaning, and at scale, such ambiguous cases are likely to be either discarded or forced into a binary category (harmful/child-coded), erasing the need for human review.
- **Loss of spatial context**: Region-level annotations (e.g., which part of an image is "threatening") are aggregated into image-level labels, making it impossible for systems to localize risk—critical for targeted content moderation.
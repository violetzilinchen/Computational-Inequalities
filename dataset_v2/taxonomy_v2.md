# Content Label Taxonomy v2 (Full Dataset Annotation)
## Core Label Definitions & Judgment Rules
1. **Familiar-Character/IP**: Well-known film, animation, cartoon characters, or intellectual property. Specific character names must be specified.
2. **Child-Coded**: Content style, characters, and scenes explicitly targeted at children (e.g., Peppa Pig, Snoopy, and other toddler-oriented cartoon styles/themes).
3. **Adult-Inappropriate**: Content unsuitable for minors (e.g., intimate/transboundary physical contact, adult-oriented language/scenes). Specific inappropriate scenarios must be detailed.
4. **Violence/Conflict**: Visible chase, attack, physical conflict, or other violent/conflicting actions in the frame. Mark the action area if applicable; do not mark if no visible actions.
5. **Threat/Intimidation**: Character expressions or frame composition that convey deterrence or threat (e.g., grim expressions, oppressive framing).
6. **Creepy-Setting**: Horror or eerie scenes (e.g., oppressive backgrounds such as pipes, black boxes, or dark walls).
7. **Unclear/Needs-Context**: Insufficient information from a single frame to determine if violence, horror, or age-inappropriate content exists. Note that "additional frames/context verification is required".
8. **Packaging/Text**: Text or UI elements in the frame (e.g., titles, channels, subtitle bars, buttons, platform logos). Specific element types must be specified.
9. **Optional Labels**: Added only when "single-frame information is insufficient for full determination". Supplementary information required for judgment must be provided.

---

## 01 freddy_fnaf_animation_horror_01.png
- Familiar-Character/IP (Blue Rabbit Character Body)
- Threat/Intimidation (Oppressive frame composition and aggressive character expression)
- Creepy-Setting (Background elements including pipes, black boxes, and dark walls)
- Packaging/Text (Subtitle bar, title, channel information, and button area)

---

## 02 pokemon_3d_dragon_anime_commentary_02.png
- Familiar-Character/IP (Pikachu and other Pokémon subjects)
- Packaging/Text (Chinese title, hashtags, and channel information)
- Unclear/Needs-Context (A single frame cannot confirm the presence of violence or age-appropriate content; additional footage is required for verification)

---

## 03 shinchan_new_episode_english_subtitles_03.png
- Familiar-Character/IP (Shin-chan and adult characters)
- Adult-Inappropriate (Intimate/transboundary physical contact in key character interaction areas, which is unsuitable for minors)
- Packaging/Text (Subtitle bar, title, and channel area)
- Optional - Mismatch (Label if the packaging has a childlike visual style but the content is age-inappropriate; exclude if the channel is explicitly adult-oriented)

---

## 04 rickMorty_vindicators_compilation_04.png
- Familiar-Character/IP (Rick, Morty)
- Packaging/Text (Identifying information including title, channel "Adult Swim")
- Unclear/Needs-Context (No violence in this frame, but the show is generally adult-oriented; additional context is required for full assessment)

---

## 05 pokemon_evolution_animated_explained_05.png
- Familiar-Character/IP (Pokémon subjects and key characters)
- Packaging/Text (Title, channel information, captions, and tags)
- Unclear/Needs-Context (Thumbnails alone cannot determine if conflicting, scary, or age-inappropriate elements are present)

---

## 06 tomAndJerry_megaCompilation_vol7_06.png
- Child-Coded (Explicitly child-oriented style and theme)
- Familiar-Character/IP (Tom)
- Violence/Conflict (Mark only when visually identifiable chase or attack actions are present in the frame; specify the action area if applicable; do not mark if no visible actions)
- Packaging/Text (UI elements including headers, channel information, and progress bars)

---

## 07 peppaPig_holidayAdventure_fullEpisodes_07.png
- Child-Coded (Peppa Pig and her brother George, toddler-oriented content)
- Familiar-Character/IP (Peppa Pig, George)
- Packaging/Text (Subtitle bar, title, and channel area)

---

## 08 snoopy_beagleScout_snoopyShow_appleTV_08.png
- Child-Coded (Overall child-oriented scenes featuring Snoopy and Woodstock)
- Familiar-Character/IP (Snoopy, Woodstock)
- Packaging/Text (Title, channel information, and Apple TV+ identifier)

---

## 09 littleFox_peterRabbit_benjaminBunny_bedtimeStories_09.png
- Familiar-Character/IP (Peter Rabbit, Benjamin Bunny)
- Child-Coded (Bedtime story style and visuals targeted at young children)
- Packaging/Text (Title and channel information)
- Optional - Unclear/Needs-Context (Insufficient visual information; additional frames are required to verify if conflicting or scary elements are present)

---

## 10 weBareBears_assemblyRequired_fullEpisode_cartoonNetwork_10.png
- Child-Coded (Three bear protagonists and cartoon-style visuals)
- Familiar-Character/IP (We Bare Bears characters: Grizzly, Panda, Ice Bear)
- Packaging/Text (Title, channel information, and playback UI elements)
- Optional - Unclear/Needs-Context (To assess "dangerous imitation potential", thumbnail evidence alone is insufficient; additional episode context is required)
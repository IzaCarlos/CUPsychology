# Contribution Guidelines

These guidelines are general conventions to help new lines fit naturally into the game rather than strict rules, feel free to play with voice, phrasing, and rhythm.

## 1. General Voice & Pacing

- **Readable at a glance**: In-game speech bubbles stay up for roughly 2.5–4.5 seconds. Short-to-medium lines (around 4–14 words) tend to read best, though an occasional longer or single-word reaction works fine when it fits the moment (e.g. pain, frustation tics, etc.).
- **Grounded tone**: Aim for tired, stressed, or dissociating survivors rather than polished hero quips, memes, or over-the-top melodrama, this is a cave where they'll most likely die.
- **Punctuation & cadence**: Ellipses (`...`), dashes, and fragments are great for trailing thoughts or caught breath; exclamation marks hit harder when saved for acute pain, panic, or sudden shocks. Try to be spare with exclamation marks (except for Dune) and Question marks (e.g. `"YAYY!!!!!!!"`)
- **Dynamic stuttering**: You don't need to add stutters (`"H-help..."`) into every distressed line. When average pain goes above 70% or valence drops below -50, the mod automatically injects stutters and trailing gasps, but the occasional manual stutter where it genuinely suits a line is fine (e.g. fear).

## 2. Dynamic Placeholders

Vanilla's `Talker` supports one placeholder in dialogue lines:

| Tag | Replaced With | Example |
|---|---|---|
| `<limb>` | Injured body part (`left forearm`, `abdomen`, `jaw`) | `"...Can't put weight on my <limb>..."` |

Other custom tags aren't parsed by the engine, so stick to `<limb>` when referencing a specific body part. (e.g.)

## 3. File & Character Layout

Main localization and dialogue live in `Assets/CasualtyPsychology/<LANG>.json`, and optional addon locales live in `Assets/CasualtyPsychology/Addons/<Addon>.locale.json`.

Inside `character`:

- **`character[0]`**: **Expie** (fallback for modded characters)
- **`character[1]`**: **Milky**
- **`character[2]`**: **Dune**

If a key is missing or empty for Milky or Dune, the mod automatically falls back to Expie's pool for that key. Place character-specific lines in that character's object to override or expand their voice.

```json
{
  "name": "Casualty Psychology",
  "description": "Mod description",
  "character": [
    {
      "psychology_frustation": [
        "...",
        "Why...",
        "Tch.",
        "Come on..."
      ]
    },
    {},
    {}
  ],
  "moodle": {
    "panicking": "Panic",
    "panickingdsc": "Heart racing and breath catching. Shaking too hard to stay steady."
  },
  "ui": {
    "psychology_dossier_item_name": "Clinical Intake Dossier"
  }
}
```

## 4. Before Opening a PR

1. **Valid JSON**: Ensure UTF-8 encoding, no trailing commas, and properly escaped quotes (`\"`). You can check locally with:
   ```bash
   python -m json.tool path/to/file.json > /dev/null
   ```
2. **Existing keys**: Stick to existing trigger keys unless engine support is being added alongside them.
3. **Variety**: Having at least a few variations per dialogue key helps keep repeated triggers from feeling stale.
4. **Focused PRs**: Grouping changes by language, character, or addon makes review much easier.
5. **No added keys**: Unless suggested, do not add new keys to the JSON.

## 5. Useful resources

- [Chicago Manual Of Style](https://www.chicagomanualofstyle.org/home.html) - Style, mechanics, and dialogue punctuation standard.
- [Purdue OWL: Quotation Marks & Dialogue](https://owl.purdue.edu/owl/general_writing/punctuation/quotation_marks/index.html) - Spoken lines, speech tags, and punctuation placement.
- [Hemingway Editor](https://hemingwayapp.com/) - Quick readability checker to cut filler and keep speech short.
- [TV Tropes: Dialogue Subtext](https://tvtropes.org/pmwiki/pmwiki.php/Main/Subtext) - Writing unspoken tension and indirect communication under stress.

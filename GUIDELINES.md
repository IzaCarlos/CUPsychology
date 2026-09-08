# Contribution Guidelines

## 1. Dialogue Style & Tone

Casualty Psychology is about desperate underground survival and cognitive collapse.

- **Short & punchy**: In-game speech bubbles display for 2.5-4.5s. Aim for 4 to 12 words per line.
- **Gritty and restrained**: Speak like an exhausted survivor in a hostile pit. No anime tropes, action-hero quips, or memes.
- **Punctuation**: Use ellipses (`...`) for breathing pauses, fading thoughts, or pain. Exclamation marks are for acute agony, weapon jams, or sheer panic.

## 2. Dynamic Placeholders

Only one dynamic token exists in dialogue lines:

| Tag | Replaced With | Example |
|---|---|---|
| `<limb>` | Injured body part (`left forearm`, `abdomen`, `jaw`) | `"...Can't put weight on my <limb>..."` |

Vanilla's `Talker` automatically substitutes `<limb>` with the affected limb name. Do not invent other placeholder tags.

## 3. Character Structure

Dialogue lives in `Assets/CasualtyPsychology/<LANG>.json` under the `character` array:

- **`character[0]`**: **Expie** (Default survivor; base lines)
- **`character[1]`**: **Milky** (WIP - currently blank; defaults to Expie's lines)
- **`character[2]`**: **Dune** (WIP - currently blank; defaults to Expie's lines)

The other characters (Milky and Dune) are currently Work-In-Progress and will automatically fall back to Expie's lines for any keys that are blank or missing in their dictionary. When writing character-specific lines, place them in that character's dictionary to override the default.

```json
{
  "name": "Casualty Psychology",
  "description": "Mod description",
  "character": [
    {
      "psychology_injury": [
        "...Took a hit.",
        "...Shit, that hurts.",
        "...Gnh... won't go down easy."
      ]
    },
    {},
    {}
  ],
  "moodle": {
    "panicking": "Acute Panic",
    "panickingdsc": "Autonomic shock response."
  },
  "ui": {
    "psychology_dossier_item_name": "Clinical Intake Dossier"
  }
}
```

## 4. PR Checklist

1. Valid JSON (no trailing commas, escaped quotes `\"`).
2. Existing trigger keys only (do not invent new key names without mod engine support).
3. At least 4 variations per dialogue key to keep survivor speech varied.
4. Keep PRs focused on one language or theme so review stays quick.

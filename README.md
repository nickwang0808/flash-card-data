# Flash Card Data

Spanish vocabulary flash cards for spaced repetition practice.

## Project Structure

```
flash-card-data/
├── spanish-vocab/
│   └── cards.json
└── README.md
```

## Card Schema

Each `cards.json` includes a `$schema` reference for VS Code validation and is keyed by the raw term (TTS-readable). The JSON key doubles as the front of the card.

```json
{
  "$schema": "https://raw.githubusercontent.com/nickwang0808/flash-card/master/schema/cards.schema.json",
  "¿Cómo estás?": {
    "back": "How are you?\n\n*¡Hola! ¿Cómo estás hoy?*\n\n> Informal, use ¿Cómo está? for formal",
    "tags": ["greetings"],
    "created": "2025-02-03T00:00:00Z",
    "reversible": true,
    "state": null,
    "reverseState": null
  }
}
```

### `back` Field Format (Markdown)

The `back` field is a markdown string combining translation, example, and notes:

```
translation text
                          ← blank line
*Example sentence here*   ← italic
                          ← blank line
> Notes or context here   ← blockquote (optional)
```

- **Line 1**: English translation (plain text)
- **Example**: Wrapped in `*italics*`, separated by a blank line
- **Notes**: As `> blockquote`, separated by a blank line (optional)

### Required Fields

| Field | Description |
|-------|-------------|
| `back` | Markdown string (translation + example + notes) |
| `created` | ISO 8601 timestamp |

### Optional Fields

| Field | Description |
|-------|-------------|
| `front` | Markdown for front side (defaults to the JSON key if omitted) |
| `tags` | String array for filtering (can be `[]`) |
| `reversible` | Set `true` for bidirectional practice (default `false`) |
| `suspended` | Set `true` to suspend from review |
| `state` | FSRS scheduling state — always `null` for new cards (managed by app) |
| `reverseState` | FSRS reverse scheduling state — always `null` for new cards (managed by app) |

The JSON key is the raw term. Spaces, accents, and special characters (¿, ñ, etc.) are fine.

## Workflow

1. **Read existing cards** - Check `<deck>/cards.json` for duplicates
2. **Create branch** - `cards/<topic>`
3. **Add cards** - Append to `cards.json`
4. **Commit** - `add <topic> vocabulary`
5. **Open PR** - List added cards in description

## Rules

- Skip existing keys (check all decks first); you may update existing cards if adding words with multiple translations
- Include examples in the `back` field when possible (as `*italic*`)
- Set `reversible: true` for words good for both directions
- One topic per PR to keep diffs reviewable
- **Irregular verbs: only create conjugation cards for actually irregular forms.** Strip out any conjugation that follows regular -ar/-er/-ir patterns (see detailed rules below)

## Irregular Verb Conjugations

### When to Create Conjugation Cards

Only for forms that are actually irregular. Skip regular forms of irregular verbs.

**What counts as irregular:**
- Stem changes (e→ie, o→ue, e→i, u→ue)
- Spelling changes (c→zc, g→j, etc.)
- Completely irregular forms (soy, voy, etc.)
- Irregular preterite stems (tuve, pude, hice)
- Irregular future/conditional stems (tendré, pondré)

**Do NOT create cards for:**
- Regular forms of irregular verbs — if the conjugation follows standard -ar/-er/-ir endings applied to the normal stem, skip it
- Nosotros forms when they follow regular pattern
- Regular future/pretérito of stem-changing verbs (e.g., dormiré, dormirás are regular -ir future — skip)
- Regular presente continuo when the gerund is regular (e.g., durmiendo is irregular → keep, but cortando is regular → skip)

### Conjugation Card Format

```json
{
  "dormir (yo, presente)": {
    "back": "duermo\n\n> o→ue stem change",
    "tags": ["verbs", "conjugations", "stem-change"],
    "created": "2025-02-03T00:00:00Z",
    "state": null,
    "reverseState": null
  }
}
```

### Tenses to Check

- presente
- pretérito
- futuro
- presente continuo (if irregular)

### Persons

yo, tú, él/ella/usted, nosotros/nosotras, ellos/ellas/ustedes

### Examples

**dormir (o→ue, present only):**
- Create cards for: duermo, duermes, duerme, duermen
- Skip: dormimos (regular)

**tener (multiple irregularities):**
- Presente: tengo, tienes, tiene, tienen
- Pretérito: all forms (tuv- stem)
- Futuro: all forms (tendr- stem)

### Card Guidelines

**Base verb card:**
- Include example in `back` as `*italic*`
- Add notes about irregularity type as `> blockquote`
- Tags: `["verbs", "<topic>"]`

**Conjugation cards:**
- `back` is just the conjugated form (no example needed)
- Optionally add irregularity type as `> blockquote` note
- Tags: `["verbs", "conjugations", "<topic>"]`

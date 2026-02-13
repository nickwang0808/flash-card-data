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

Each card in `cards.json`:

```json
{
  "¿Cómo estás?": {
    "source": "¿Cómo estás?",
    "translation": "How are you?",
    "example": "¡Hola! ¿Cómo estás hoy?",
    "notes": "Informal, use ¿Cómo está? for formal",
    "tags": ["greetings"],
    "created": "2025-02-03T00:00:00Z",
    "reversible": true,
    "state": null,
    "reverseState": null
  }
}
```

### Required Fields

| Field | Description |
|-------|-------------|
| `source` | Word/phrase as-is (also used as JSON key) |
| `translation` | English translation |
| `tags` | Tags for filtering (can be `[]`) |
| `created` | ISO8601 timestamp |
| `reversible` | Set `true` for bidirectional practice |
| `state` | Always `null` for new cards |
| `reverseState` | Always `null` for new cards |

### Optional Fields

| Field | Description |
|-------|-------------|
| `example` | Example sentence |
| `notes` | Context, regional variations |

The JSON key and `source` field should be identical. Spaces, accents, and special characters (¿, ñ, etc.) are fine.

## Workflow

1. **Read existing cards** - Check `<deck>/cards.json` for duplicates
2. **Create branch** - `cards/<topic>`
3. **Add cards** - Append to `cards.json`
4. **Commit** - `add <topic> vocabulary`
5. **Open PR** - List added cards in description

## Rules

- Skip existing keys (check all decks first); you may update existing cards if adding words with multiple translations
- Include examples when possible
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
    "source": "dormir (yo, presente)",
    "translation": "duermo",
    "tags": ["verbs", "conjugations", "stem-change"],
    "created": "2025-02-03T00:00:00Z",
    "reversible": false,
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
- Include example sentence
- Add notes about irregularity type
- Tags: `["verbs", "<topic>"]`

**Conjugation cards:**
- No example needed
- Tags: `["verbs", "conjugations", "<topic>"]`
- Notes optional: can mention irregularity type

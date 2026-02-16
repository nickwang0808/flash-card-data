# Spanish Vocab

## Rules

- Set `reversible: true` for single-word translations
- Include Spanish examples in `front` field (as `*italic*`), not in `back` — keeps languages separated so reverse cards don't leak the answer
- If a card has no example sentence, omit the `front` field (defaults to the key)
- Add English notes as `> blockquote` in `back` when useful
- Tags: `["greetings"]`, `["verbs"]`, `["food"]`, etc.
- **Irregular verbs: only create conjugation cards for actually irregular forms.** Skip any conjugation that follows regular -ar/-er/-ir patterns

## Field Convention

**`front`** (optional — omit if no example sentence, defaults to key):
```
key text
                          <- blank line
*Spanish example sentence*   <- italic
```

**`back`** (English only):
```
translation text
                          <- blank line (if note follows)
> Notes or context here   <- blockquote (optional, English)
```

## Irregular Verb Conjugations

### When to Create Conjugation Cards

Only for forms that are actually irregular. Skip regular forms of irregular verbs.

**What counts as irregular:**
- Stem changes (e->ie, o->ue, e->i, u->ue)
- Spelling changes (c->zc, g->j, etc.)
- Completely irregular forms (soy, voy, etc.)
- Irregular preterite stems (tuve, pude, hice)
- Irregular future/conditional stems (tendre, pondre)

**Do NOT create cards for:**
- Regular forms of irregular verbs
- Nosotros forms when they follow regular pattern
- Regular future/preterito of stem-changing verbs
- Regular presente continuo when the gerund is regular

### Conjugation Card Format

```json
{
  "dormir (yo, presente)": {
    "back": "duermo\n\n> o->ue stem change",
    "tags": ["verbs", "conjugations", "stem-change"],
    "created": "2025-02-03T00:00:00Z"
  }
}
```

### Tenses to Check

- presente
- preterito
- futuro
- presente continuo (if irregular)

### Persons

yo, tu, el/ella/usted, nosotros/nosotras, ellos/ellas/ustedes

### Examples

**dormir (o->ue, present only):**
- Create cards for: duermo, duermes, duerme, duermen
- Skip: dormimos (regular)

**tener (multiple irregularities):**
- Presente: tengo, tienes, tiene, tienen
- Preterito: all forms (tuv- stem)
- Futuro: all forms (tendr- stem)

### Card Guidelines

**Base verb card:**
- Include Spanish example in `front` as `*italic*`
- Add English notes about irregularity type as `> blockquote` in `back`
- Tags: `["verbs", "<topic>"]`

**Conjugation cards:**
- `back` is just the conjugated form (no example needed)
- Optionally add irregularity type as `> blockquote` note
- Tags: `["verbs", "conjugations", "<topic>"]`

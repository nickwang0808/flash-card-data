# Spanish Vocab

## Rules

- Set `reversible: true` for single-word translations
- Include examples in `back` when possible (as `*italic*`)
- Add notes as `> blockquote` when useful
- Tags: `["greetings"]`, `["verbs"]`, `["food"]`, etc.
- **Irregular verbs: only create conjugation cards for actually irregular forms.** Skip any conjugation that follows regular -ar/-er/-ir patterns

## `back` Field Convention

```
translation text
                          <- blank line
*Example sentence here*   <- italic
                          <- blank line
> Notes or context here   <- blockquote (optional)
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
- Include example in `back` as `*italic*`
- Add notes about irregularity type as `> blockquote`
- Tags: `["verbs", "<topic>"]`

**Conjugation cards:**
- `back` is just the conjugated form (no example needed)
- Optionally add irregularity type as `> blockquote` note
- Tags: `["verbs", "conjugations", "<topic>"]`

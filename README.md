# rigatech-data

**Open data repository for [riga.tech](https://riga.tech)** — the Riga / Baltic IT ecosystem catalog: events, jobs, courses, and ecosystem resources, stored as one JSON file per entry.

Everything here is openly licensed and machine-readable. Anyone can fork, mirror, or build on this dataset.

## Layout

```
events/                            # one .json per event, filename = slug
jobs/                              # one .json per job, filename = slug
courses/                           # one .json per course, filename = slug
resources/
  ├─ accelerators/
  ├─ vcs/
  ├─ coworking/
  ├─ communities/
  ├─ education/
  ├─ media/
  └─ tooling/
```

`courses/` holds individual programs you can enroll in — cohort bootcamps, online tracks, self-paced lab series. `resources/education/` holds the *institutions* (schools, academies). A course's `provider` is free text and may point at a resource, but is not a foreign key.

Resource category = parent directory name.

## Adding content

1. Pick the right directory.
2. Copy an existing file as a template.
3. The filename (without `.json`) is the slug.
4. Every text field that ends up on screen needs both `en` and `lv` values.
5. Dates are ISO 8601 (`2026-04-15`). Tags are lowercase, no spaces.

## Schema conventions

- **Slug** — kebab-case, ASCII-folded from any diacritics (e.g. `ā→a`, `š→s`, `č→c`), no leading/trailing dashes, ≤ 80 characters. Must match the filename without the `.json` extension.
- **Enums** — lowercase, exact spelling. Examples: `remote ∈ {onsite, hybrid, remote}`, `employment ∈ {full-time, part-time, contract, intern}`, `seniority ∈ {junior, mid, senior, staff, lead}`.
- **URLs** — fully-qualified, must start with `https://`.
- **Summaries** — bilingual `{lv, en}` objects, one or two sentences each.
- **Tags / stack** — lowercase, kebab-case, no whitespace (`react`, `postgres`, `data-engineering`).
- **Salary** — formatted as `€<from>–<to>` (en-dash, e.g. `€2500–3500`) or `€<amount>+` for an open-ended floor. Omit the field entirely when no salary is published.

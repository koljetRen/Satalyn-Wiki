# Satalyn Wiki — rules for every session

This repo is a wiki for **Satalyn**, a fantasy world (the name is a placeholder) used for D&D campaigns and for the novel series *The Runaways* and its spin-offs. It is built with Quartz 5: Markdown files in `content/` become the website. Read this file fully before writing anything.

## Folder layout

| Path | What it is | Published on the site? |
| --- | --- | --- |
| `sources/` | Raw notes imported from the author's Google Drive and Claude doc. **Read-only.** Never edit; cite instead. `sources/README.md` lists every source, its date, and known gaps. | No |
| `content/` | The wiki itself. One page per subject. | Yes |
| `content/private/` | Author-only material (see Secrets). Excluded by `ignorePatterns`. | No |
| `templates/` | Page templates. Copy one when starting a page. | No |
| `WIKI-PLAN.md` | The work packages and their status. Update your package's row when you finish. | No |
| `quartz/`, `quartz.config.yaml`, `package*.json` | The Quartz engine and its settings. Don't touch unless the task is about the site itself. | — |

Sections inside `content/` (each has an `index.md` that introduces it):

- `cosmology/` — the multiverse, castes, the Book of Creation, the seven phases, sacred creatures
- `gods/` — the pantheon (one page per deity) and lesser/regional gods
- `religion/` — worship practices, festivals, regional faiths (Skyfather spirits, Aegryamis brother gods, Xi ancestor worship, Osisu ocean goddess)
- `magic/` — how magic works, bloodlines, wizards, magical materials
- `history/` — timeline, eras (golden age, ice age, Xi Empire, fall of Fillyolia), major events and battles
- `peoples/` — races (`peoples/races/`) and cultures (`peoples/cultures/`)
- `places/` — regions, cities, geographic features
- `characters/` — named people, one page each
- `organizations/` — the Resistance, the slave hunters, King Carter's forces, councils
- `nature/` — plants, animals, monsters
- `things/` — materials (xiramite), currency, notable objects
- `stories/` — the books and campaigns themselves: premise, cast, plot outline

## Page rules

1. **File names:** lowercase, hyphens, no spaces: `content/characters/eric.md`. The page title goes in frontmatter `title:` with proper capitals.
2. **Frontmatter** on every page (see `templates/`): `title`, `aliases` (alternate spellings and old names), `tags`, `status` (`stub` | `draft` | `canon`), `sources` (list of `sources/...` paths the page is based on).
3. **Links:** use Obsidian wikilinks `[[Page Title]]` or `[[file-name|shown text]]`. Link the first mention of every person, place, god, culture, race or thing that has (or should have) its own page. A link to a page that doesn't exist yet is fine: it marks a page to write.
4. **Lead sentence first:** the first sentence says what the subject is ("Eric is the protagonist of *The Runaways*, a warrior and wizard of Xi descent raised in Aramore."). Then short sections. Use the template's headings; drop the ones with nothing to say.
5. **Only what the notes say.** Do not invent lore. Rephrase and organize the author's notes; don't add new facts, names, dates or motives. When the notes hint at something ("possible", "idea:", "maybe"), keep it labeled as an idea, e.g. under `## Ideas and open threads`. If a gap is obvious, add it to `## Open questions` instead of filling it.
6. **Cite sources:** end each page with `## Sources`, listing the `sources/...` files used (plain text paths, not links).
7. **Voice:** encyclopedic, present tense for things that are true in the world's "now" (around year 1067, the start of *The Runaways*), past tense for history. Plain words. British/American spelling: follow the source (the Claude doc uses British spelling; keep whichever the page's main source uses).
8. **Tables** for lists of attributes (e.g. the coin values, the prison roster). Callouts (`> [!note]`) for asides.

## Canon and conflicting notes

The notes were written over five years (2020–2026) and often disagree. Rules:

1. **Newer wins for the main text**, in this order (newest first):
   1. `sources/claude-doc/world-creation-notes.md` (Oct 2026) — cosmology, gods, magic, races, ice age
   2. `sources/drive/organized-runaways-notes.md` (Apr 2026) — cultures, regions, characters, plants, names
   3. `sources/drive/runaways/runaways-ideas.md` (content mostly 2024) — Runaways plots, character arcs, Xi, money
   4. everything else (2021–2025)
2. **Never silently drop the older version.** Put it in a `> [!info] Canon note` callout on the page: what the older note said and where. Example: Krarkur is "God of Deceit" in the 2026 doc but "God of War" in the older Runaways ideas list.
3. **Spelling variants** go in `aliases` (e.g. `Kurupal` / `Krerupal`, `Xander` / `Zandar`, `Aegryamis` / `Aegyramis`). Use the newest spelling as the title.
4. Add every conflict you find to `content/private/open-questions.md` under its section, so the author can rule on it.

Known conflicts (already spotted — handle as above):

- Krarkur: God of Deceit (2026) vs God of War (older). Ozefio: Goddess (2026) vs God (older). Dauviti: God of the Dead vs God of the Underworld. Modingua: "Goddess of Motherhood, love, fertility and reproduction" vs "Goddess of Mothership" (typo for Motherhood).
- Magic: iron in the blood, bloodline from Magurkai's 100 villagers (2026) vs DNA-based capacity, one of four elements (air, earth, water, fire), restored by rest (older). These may be compatible — present the 2026 model and note the older details as possibly still true.
- Race name: Kurupal (2026) vs Krerupal (older Runaways notes).
- King Carter's city: Carthollow (2026 sheet) vs Carterville (older). Eric's prison: Carthollow Dungeon.
- David: "dies in chapter 1" in a prison skirmish (2026 sheet) vs betrays the resistance and later sacrifices himself for Eric in Book 3 (older plot).
- Resistance leader: Xander / Zandar; killed by Elliott (Book 3 plot) or by Tahir (character notes) — Elliott's alternate name is Tahir in one note and Rewis in another.
- King Augo: King of Keyesport Vale (character list) vs rightful heir of Fillyolia and Carter's brother/cousin (plot twist notes); Book 2 blurb says "King [Argo?]".
- Akio vs Aiko; Rannulfr / Rannulfer / Rann; Samheir / Samhier / Sam; Aerlem / Aerelm.
- "Aerelm" is a resistance wizard in the Runaways notes, but the D&D note says "Magic is banned from Aerelm because the King is worried about power" — possibly a place. Flag it; don't merge.
- Peter Snyder (slave book): eldest son vs second son; "nation of Snyder" vs "throne of Forin".

## Secrets (author-only material)

**Audience:** right now only the author reads the site. **Later it will be opened to everyone** (players and readers). So write every page to be safe for the public, with one exception: secrets.

Secrets are things people in the world don't know (e.g. the sacred creatures are really the gods' true forms), book plot twists and spoilers, and DM-only information. Write them on the normal page inside a folded callout at the end, just above `## Sources`:

```markdown
> [!warning]- Secrets (author only)
> The sacred creatures don't live on the world: they are the gods' true forms...
```

**Always use exactly that callout header, and never put a secret anywhere else on a page** (not in the lead, tables, captions or other pages' summaries). Before the site goes public, a session will move every one of these callouts into `content/private/` mechanically, so a secret outside the callout would leak. A page that is entirely secret goes straight into `content/private/` (same subfolder layout as `content/`).

## Working in parallel

Several sessions may work at once, each on one package from `WIKI-PLAN.md`. To avoid collisions:

- Only create or edit pages inside your package's folders. If you need a page from another package to exist, just link to it.
- Shared files (`content/index.md`, section `index.md` files outside your package, `content/private/open-questions.md`) — append only; never rewrite others' lines.
- Commit often with clear messages, e.g. `Add gods: the Nine`. Work on your own branch named after your package and open a pull request when done (unless told to push directly).

## Building the site

`npm ci`, then `npx quartz plugin install`, then `npx quartz build --serve` to preview at http://localhost:8080. Building needs network access to download plugins.

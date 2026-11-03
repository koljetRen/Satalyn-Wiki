# Wiki build plan

Every package below can run in its own Claude Code cloud session **at the same time**. Each one reads `CLAUDE.md` and `sources/`, writes only inside its own folders, and opens a pull request. After wave 1 is merged, run wave 2.

To start a package: open a new cloud session on this repository and paste the package's prompt. Tick the status when its pull request is merged.

## Wave 1 — write the pages (run all six at once)

| # | Package | Folders it owns | Main sources | Status |
| --- | --- | --- | --- | --- |
| 1 | Cosmos, gods and religion | `cosmology/`, `gods/`, `religion/` | `claude-doc/world-creation-notes.md`, religion parts of `runaways-ideas.md` and `organized-runaways-notes.md` | [ ] |
| 2 | Magic, history and things | `magic/`, `history/`, `things/` | `claude-doc/world-creation-notes.md`, `runaways-ideas.md`, `runaways-character-info-personal.md` | [ ] |
| 3 | Peoples and nature | `peoples/`, `nature/` | `organized-runaways-notes.md`, `claude-doc/world-creation-notes.md` | [ ] |
| 4 | Places | `places/` | all sources (places are scattered everywhere) | [ ] |
| 5 | Main characters and organizations | `characters/` (main and named supporting cast), `organizations/` | `runaways-character-info-personal.md`, `runaways-ideas.md`, `organized-runaways-notes.md`, `the-runaways-ideas-personal.md`, `resistance-leadership-personal.md` | [ ] |
| 6 | Stories, minor characters and the D&D notes | `stories/`, `characters/` (prison inmates and guards, slave-book cast only) | `runaways-ideas.md`, `slave-hunters/*`, `runaways-background-characters.md`, `book-2-stomped-in-the-dust.md`, `notes-from-dnd-about-my-world.md` | [ ] |

## Wave 2 — make it one wiki (after wave 1 is merged)

| # | Package | What it does | Status |
| --- | --- | --- | --- |
| 7 | Links and consistency | Find every `[[link]]` with no page and either write a stub or fix the link; make names and aliases consistent across packages; merge duplicate pages; fill in section `index.md` pages with lists of their pages; tidy `content/private/open-questions.md` | [ ] |
| 8 | Timeline and overview pages | A full timeline page from creation to 1074; a "World at a glance" page; a "Who's who in *The Runaways*" page; a pantheon table | [ ] |
| 9 | Site and deploy | Build the site, fix any build errors, pick colors/fonts, set the real `baseUrl`, add the hosting setup (Cloudflare Pages or GitHub Pages), add map images if the author has uploaded them | [ ] |

## Prompts

### Package 1 — Cosmos, gods and religion

```text
Read CLAUDE.md fully, then sources/README.md. You are doing Package 1 of WIKI-PLAN.md: Cosmos, gods and religion.
Write wiki pages in content/cosmology/, content/gods/ and content/religion/ from the notes in sources/ — mainly sources/claude-doc/world-creation-notes.md, plus the religion and god-list sections of sources/drive/runaways/runaways-ideas.md and the Religion rows of sources/drive/organized-runaways-notes.md.
Pages to write at least: the multiverse and its castes; the Book of Creation; the seven phases of creation (one page, with a section per phase); the sacred creatures; one page per deity (Euiklatz, Lebarka, Modingua and each of the Nine); "The Nine" overview; the pantheon overview (still unnamed); lesser and regional gods (Aegryamis's two brother gods, the Osisu ocean goddess, Aramore/Skarg Skyfather and elemental spirits, Xi ancestor worship); worship through dance and song; the Creation Festival; why worship faded; the gods in the modern day.
Use the templates in templates/. Follow the canon, secrets and citation rules in CLAUDE.md exactly — no invented lore. Log conflicts in content/private/open-questions.md.
Work on a branch named package-1-cosmos, commit as you go, and open a pull request when done. Tick package 1 in WIKI-PLAN.md in that PR.
```

### Package 2 — Magic, history and things

```text
Read CLAUDE.md fully, then sources/README.md. You are doing Package 2 of WIKI-PLAN.md: Magic, history and things.
Write wiki pages in content/magic/, content/history/ and content/things/ from sources/.
Pages to write at least: magic (overview); bloodline magic and the iron in the blood; overcasting; wizards (who can become one and how they train — link to [[Council of Worldly Wizards]], which Package 5 writes); dormant bloodlines (Eric, Dherlin); magic bans (the D&D note about Aerelm); xiramite (how it cracks and connects, Xi blood, Eric's sword and Lucas's dagger); the coinage (Parce, Darceo, Reso, Augist, Pagon — with a conversion table); the golden age (phase six); the ice age; the ice age people; the Xi Empire (350–430); the fall of Fillyolia; Dherlin's attacks on the Great City (1045); the desolation of the ground water; the timeline of the Runaways years (1067–1074). Battles from the books (Misty Phlats, the fort, the island prison, Carterville/Carthollow) go in history/ as event pages.
Use the templates in templates/. Follow the canon, secrets and citation rules in CLAUDE.md exactly — no invented lore. Log conflicts in content/private/open-questions.md.
Work on a branch named package-2-magic-history, commit as you go, and open a pull request when done. Tick package 2 in WIKI-PLAN.md in that PR.
```

### Package 3 — Peoples and nature

```text
Read CLAUDE.md fully, then sources/README.md. You are doing Package 3 of WIKI-PLAN.md: Peoples and nature.
Write wiki pages in content/peoples/races/, content/peoples/cultures/ and content/nature/ from sources/ — mainly sources/drive/organized-runaways-notes.md and sources/claude-doc/world-creation-notes.md.
Pages to write at least: one page per race (humans, Kurupal/Krerupal, elves, stoneskins, owl-antlered folk) and the ice age people; the Kurupal–stoneskin rivalry; one full page per culture using every column of the Cultures sheet (Xi, Osisu, Dyken, Aramore, Aegryamis, Skarg), including each culture's real-world name sources from the Names sheet; plants (Thrym Pine, Akyethis Tree, Colored Corn); creatures (Stormshark, Ozefio's sea "pets"/sea monsters). Note where the notes hint at other peoples (merfolk, dwarves/goliaths descending from ice age people) as ideas, not facts.
Use the templates in templates/. Follow the canon, secrets and citation rules in CLAUDE.md exactly — no invented lore. Log conflicts in content/private/open-questions.md.
Work on a branch named package-3-peoples, commit as you go, and open a pull request when done. Tick package 3 in WIKI-PLAN.md in that PR.
```

### Package 4 — Places

```text
Read CLAUDE.md fully, then sources/README.md. You are doing Package 4 of WIKI-PLAN.md: Places.
Write wiki pages in content/places/ from every file in sources/ — place names are scattered across all of them, so read them all.
Pages to write at least: regions (Aramore, Skarg, Dyken, Osisu, Aegryamis, Xi, Cadnitz, Fillyolia, the Great Desert, the Misty Peaks / Southern Misty Mountains, the North Spine, Shadow Bay, Dyke Hills, the North Sea, Thrymfell and Thrymfell Forest, Northwatch, Aramore Forest) and settlements and sites (Carthollow / Carterville and its dungeon, Harrisonville, Misty Phlats, the resistance base and its main cavern, the Training Grove, Shadow's Edge, Mourncliff, Moonwick, Keyesport Vale, Quino, Sprake, Averill, Lucal, the island prison, the Xi city ruins, the magic holy site, Snyder/Forin). Use sources/drive/runaways/the-runaways-sites-personal.md for the list of locations the author pictured. Record the spare city names (Houghtanaba, Rayspan, Weasbourn, Waorig) on content/places/index.md as unused names, not as pages. Add a short "Map progress" page from the Claude doc's Map Progress section.
Use the templates in templates/. Follow the canon, secrets and citation rules in CLAUDE.md exactly — no invented lore, no invented geography. Log conflicts in content/private/open-questions.md.
Work on a branch named package-4-places, commit as you go, and open a pull request when done. Tick package 4 in WIKI-PLAN.md in that PR.
```

### Package 5 — Main characters and organizations

```text
Read CLAUDE.md fully, then sources/README.md. You are doing Package 5 of WIKI-PLAN.md: Main characters and organizations.
Write one page per named character of The Runaways in content/characters/ (everyone in the cast list in sources/drive/runaways/runaways-character-info-personal.md, plus Akio Stormshark, Bardon, the Torturer, Brotz, Eric's mother and the Xi warriors). Leave the 14 prison inmates other than Eric, David, Bardon, Akio and Rannulfr, the 8 prison guards other than Ulrich, and the slave-book cast to Package 6. Give each character every fact the notes hold: role, height, rank, culture, looks, arc, relationships (the Eric–Lucas–Brian family tree), and fate. Thin characters get short stub pages.
Also write content/organizations/: the Resistance (with its ranks and unit sizes as a table, and who held each rank), King Carter's forces, the council of worldly wizards, the Xi council of elders.
Use the templates in templates/. Follow the canon, secrets and citation rules in CLAUDE.md exactly — book plot twists (Brian is Eric's father, Carter's possession, Zandar's betrayal, Eric killing his mother) go in the Secrets callout. No invented lore. Log conflicts in content/private/open-questions.md.
Work on a branch named package-5-characters, commit as you go, and open a pull request when done. Tick package 5 in WIKI-PLAN.md in that PR.
```

### Package 6 — Stories, minor characters and the D&D notes

```text
Read CLAUDE.md fully, then sources/README.md. You are doing Package 6 of WIKI-PLAN.md: Stories, minor characters and the D&D notes.
Write content/stories/: The Runaways (series overview), The Runaways Book 1 (with the rewritten 30-step plot and the list of rewrite edits), Book 2: Stomped in the Dust (blurb plus the possible plot), Book 3, the slave book / Slave Hunters (Peter Snyder), the planned wizard book (1072), the joining of the series (1074), and a page for the author's D&D campaign holding the D&D notes. Put each draft prose passage from sources/drive/runaways/paragraphs-for-the-runaways-personal.md and the two scenes in runaways-ideas.md ("Revealing the Xi Daggers", "The Gladiator Battle") on a "Draft passages" page under stories/, quoted exactly.
Also write character pages in content/characters/ for the minor cast only: the prison inmates (Peng, Namacuix, Ivar, Vali, Anghus, Vlastimir, Godfrey, Samanya, Stigr), the guards except Ulrich (Skari, Cadman, Frode, Pedro, Gunter, Kayne, Ormr), and the slave-book cast (Peter Snyder, King William Snyder VII, William VIII, the head helper/council member, and Jason — known only from fragments of the handwritten pages described in sources/README.md, so keep his page to those fragments). Package 5 owns everyone else; just link to them. Put the spare name lists on a "Name bank" page in stories/.
Use the templates in templates/. Follow the canon, secrets and citation rules in CLAUDE.md exactly — no invented lore. Log conflicts in content/private/open-questions.md.
Work on a branch named package-6-stories, commit as you go, and open a pull request when done. Tick package 6 in WIKI-PLAN.md in that PR.
```

### Package 7 — Links and consistency (wave 2)

```text
Read CLAUDE.md fully. You are doing Package 7 of WIKI-PLAN.md: Links and consistency. Wave 1 is merged.
1. List every [[wikilink]] in content/ whose target page doesn't exist. For each, either fix the link to the right existing page (check aliases) or write a short stub page from sources/ in the right folder.
2. Find duplicate or overlapping pages written by different packages and merge them, keeping every fact and source.
3. Make names consistent: titles use the newest spelling, older spellings are in aliases.
4. Fill each section index.md with a grouped list of its pages and one line each.
5. Clean up content/private/open-questions.md: merge duplicates and group by topic.
Don't invent lore. Branch package-7-links, open a pull request, tick package 7.
```

### Package 8 — Timeline and overview pages (wave 2)

```text
Read CLAUDE.md fully. You are doing Package 8 of WIKI-PLAN.md: Timeline and overview pages. Wave 1 is merged.
Write, from the existing wiki pages and sources/: content/history/timeline.md (creation phases → golden age → ice age → Xi Empire 350–430 → fall of Fillyolia → 1045 → 1067–1074, with links on every entry; mark uncertain dates); content/world-at-a-glance.md (a one-page overview of the world for a new reader or player); content/stories/who-is-who.md (every Runaways character in one table: name, role, culture, allegiance, fate — fates in a Secrets callout); and a pantheon table on content/gods/index.md. Link the new pages from content/index.md.
Don't invent lore. Branch package-8-overviews, open a pull request, tick package 8.
```

### Package 9 — Site and deploy (wave 2)

```text
Read CLAUDE.md fully. You are doing Package 9 of WIKI-PLAN.md: Site and deploy.
Run npm ci, npx quartz plugin install and npx quartz build; fix any build errors or broken pages. Check the site in a browser at phone and desktop widths and fix layout problems. Ask me which host I want (Cloudflare Pages works with a private repo for free; GitHub Pages needs a public repo on the free plan), then add the matching setup, set baseUrl in quartz.config.yaml, and give me the exact clicks to connect the host. Branch package-9-site, open a pull request, tick package 9.
```

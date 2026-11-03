# Build notes

Package 9 (Site and deploy) checked the site on 3 November 2026, against `main` after wave 1 (212 Markdown files in `content/`). This file records what was checked, what was fixed, and what is still wrong but needs a content edit (left alone because Packages 7 and 8 are editing `content/` at the same time).

## Build

Commands: `npm ci`, `npx quartz plugin install`, `npx quartz build`. The build now finishes with no errors: 212 files in, about 870 files out to `public/`, in about 35 seconds.

### Fixed through configuration

| Problem | Fix |
| --- | --- |
| No `.gitignore`, so `node_modules/`, `public/` and `.quartz/` would have been committed | Added `.gitignore` |
| `npx quartz plugin install` did nothing ("No quartz.lock.json found") | Ran `npx quartz plugin install --from-config` once and committed the resulting `quartz.lock.json` (it pins the one Git plugin, the Leaflet map plugin) |
| Warning: "Could not load plugin `@quartz-community/obsidian-plugin-excalidraw`", so the plugin was skipped | Added it to `package.json` |
| Every build installed the theme package `@quartz-themes/its-theme` on the fly | Added it to `package.json` |
| The `cname` plugin wrote a `CNAME` file containing the placeholder `satalyn.example.com` (that file is for GitHub Pages only) | Disabled the plugin |
| `baseUrl` was a placeholder | Still a placeholder, now marked `TODO(hosting)`. Set it after the first Cloudflare deploy (see `HOSTING.md`, step 4) |

### Build warnings that come from content (not fixed: needs a content edit)

| File | Warning | Suggested fix |
| --- | --- | --- |
| `content/magic/index.md` and `content/magic/magic.md` | Slug collision: both become the URL `/magic/`. `magic/magic.md` wins, so **`magic/index.md` is not on the site at all**. | Merge the two into `magic/index.md` and delete or rename `magic/magic.md` (for example to `magic/how-magic-works.md`), keeping its aliases. |

## Browser check

Checked with the preinstalled Chromium (Playwright) against `npx quartz build --serve` at phone width (390 × 844) and desktop width (1280 × 800), in light and dark mode.

| What | Page | Result |
| --- | --- | --- |
| Home page | `/` | OK at both widths. No sideways scrolling. |
| Character page | `/characters/eric` | OK. Infobox table, breadcrumbs, table of contents and backlinks all render. |
| Culture page | `/peoples/cultures/xi-people` | OK |
| Folder page | `/characters/` | OK. Lists every page in the folder. |
| Search | type "Eric" | 8 results, with a preview pane on desktop. Works at both widths. |
| Graph | local graph on `/characters/eric`, then the global graph | Both draw. The global graph opens full screen at both widths. |
| Console errors | all of the above | None (see the network note below) |

**Network note:** this check ran in a sandbox that blocks `cdn.jsdelivr.net`, where the graph (d3, pixi.js) and math (KaTeX) libraries are loaded from. For the check, those files were served from local copies of the same versions. On the real site, visitors' browsers load them from the CDN as normal.

### Theme

The config started on the `its-theme` / `ttrpg-dnd` variation. On screen it had problems: the lead paragraph and other text were light green on white (hard to read), the selected page in the Explorer was grey text on dark green, and the table of contents entries were very faint. Four options were compared in light and dark mode (`ttrpg-dnd`, `ttrpg-wotc`, `ttrpg-pathfinder-remastered`, and no theme). The site now uses **`ttrpg-wotc`**: a cream "parchment" background, red headings and link highlights, and dark body text, with a readable dark mode. To try another look, change `variation:` in `quartz.config.yaml`. The other choices are `ttrpg-dnd`, `ttrpg-pathfinder`, `ttrpg-pathfinder-remastered`, `nord`, `notion`, `minimalist`, `gray`, `blue`, `drowned`, `rainbow`, `school-days`, `tangerine-dunes` and `its-dark`.

### Layout issues left as they are

- **Tags in the Properties box at phone width.** The tag pills sit in a narrow table column and wrap a few letters per line (for example "#ch / ara / cte / r"). They are still readable and clickable, and the problem doesn't occur on desktop. The obvious fix in config is to show tags with the `tag-list` component instead, but enabling `tag-list` makes the "Satalyn" site title in the left sidebar disappear (the tag list renders in its place). It was tried and reverted, and the config now has a comment explaining why. A CSS override would fix it, but that is a code change, not a config change.
- **Local graph at phone width.** It sits beside the Backlinks box at the bottom of the page and is only about 150 px wide. It works, and the full-screen graph button gives a larger view.
- **Folded Secrets callouts** show an empty strip about 34 px tall under the title while folded. The text is hidden; this is just the theme's padding.

## Private material

| Check | Result |
| --- | --- |
| `content/private/` in the output | Not there. No `public/private/` folder, no links to it, and nothing from it in the search index (`static/contentIndex.json`). |
| `templates/` in the output | Not there. `templates/` sits outside `content/`, so Quartz never reads it (it's also in `ignorePatterns`). |
| `> [!warning]- Secrets (author only)` callouts | All 74 render **folded** (`is-collapsed`), on 74 pages. They unfold when clicked. Every Secrets callout in `content/` uses the exact header from `CLAUDE.md`, and no other warning callouts exist. |
| RSS feed (`index.xml`), sitemap | No secret text |

> [!warning] Before the public launch
> Folding hides secrets on the page, but **the search index (`static/contentIndex.json`) contains the full text of every page, including the 74 Secrets callouts.** Anyone can download that file, and searching for a word that appears only inside a secret will find the page and show the matching secret text in the search preview. This is fine while only the author can see the site (see Cloudflare Access in `HOSTING.md`). The planned step of moving every Secrets callout into `content/private/` before launch fixes it. Do that step before removing the Access login.

## Repository cleanup

Removed the Quartz project's own files: `.github/` (FUNDING.yml, issue templates, dependabot.yml, pull request template, and the workflows build-preview, ci, dependabot-automerge, deploy-preview, deploy-v5 and docker-build-push) and the root `Dockerfile`. Quartz's `CODE_OF_CONDUCT.md`, `LICENSE.txt` and the `docs/` folder (Quartz's own documentation) are still there. They don't affect the site.

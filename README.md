# RuTracker EN

A userscript that translates [RuTracker](https://rutracker.org)'s interface from Russian to English: the homepage category tree, the tracker search page, and user profiles.

Torrent titles, topic titles, and usernames are left alone — only the site's own UI and category names get translated.

## What it translates

- **Homepage (`index.php`)** — the full forum category tree, sidebar boxes, news, footer
- **Tracker (`tracker.php`)** — the "go to category" tree, sort/filter options, results table
- **Profiles (`profile.php`)** — role, rank, stats, contacts, restrictions; works on any user's profile
- Dates (`23-Сен` → `23-Sep`) and relative durations (`1 год 2 месяца` → `1 year 2 months`)

## Install

1. Install a userscript manager — [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/) both work.
2. Open [`rutracker-en.user.js`](./rutracker-en.user.js), click **Raw**, and your userscript manager should offer to install it. If it doesn't, create a new script and paste the file's contents in.

## How it works

The script walks the page's text nodes and swaps any Russian string it recognizes for its English translation, using two dictionaries defined at the top of the file:

- `UI_DICT` — navigation, search form, profile labels, footer (~270 entries)
- `CATEGORY_DICT` — the full forum category tree (~1300 entries)

Matching is exact, on the whole trimmed string. Anything not in the dictionary is left untouched, which is why torrent and topic titles never need special-casing to stay in Russian.

A few extra rules cover text that mixes a label with dynamic data: Russian month abbreviations, relative durations, and count prefixes like "Search results: 500".

## Found something wrong or missing?

RuTracker has a lot of subforums, and part of the category dictionary was machine-translated, so a handful of the more obscure ones read awkwardly or got missed.

- Open an issue with the string that's wrong or missing.
- Better yet, open a pull request. Both dictionaries are plain JS objects, one entry per line, sorted alphabetically — find the Russian key and fix the English value, or add a new line if it's missing.

If this is useful to you, a star helps other people find it.

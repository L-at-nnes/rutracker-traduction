# RuTracker EN

A userscript that translates [RuTracker](https://rutracker.org)'s interface from Russian to English: the homepage category tree, forum pages, torrent pages, the tracker search page, user profiles, groups, private messages and more.

Torrent titles, topic titles, and usernames are left alone — only the site's own UI and category names get translated.

## What it translates

- **Homepage (`index.php`)** — the full forum category tree, sidebar boxes, news, footer
- **Tracker (`tracker.php`)** — the "go to category" tree, sort/filter options, results table
- **Profiles (`profile.php`)** — role, rank, stats, contacts, restrictions; works on any user's profile
- **Forum pages (`viewforum.php`)** — subforum names and descriptions, table headers
- **Torrent pages (`viewtopic.php`)** — stats banner, download/magnet buttons, compare box, display options, post dates
- **Forum search and wishlist (`search.php`)** — search form, "Future downloads" list
- **Private messages (`privmsg.php`) and editor (`posting.php`)** — folders, compose form, formatting toolbar
- **Groups (`groupcp.php`)** — group names
- **Profile editing** — form labels and the country list
- Dates (`23-Сен` → `23-Sep`) and relative durations (`1 год 2 месяца` → `1 year 2 months`)

## Install

1. Install a userscript manager — [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/) both work.
2. Click **[rutracker-en.user.js](https://raw.githubusercontent.com/L-at-nnes/rutracker-traduction/main/rutracker-en.user.js)** — your userscript manager should pick it up and prompt you to install it.

The script auto-updates from this same URL, so once installed you'll get new translations and fixes without reinstalling.

## How it works

The script walks the page's text nodes and swaps any Russian string it recognizes for its English translation, using dictionaries defined at the top of the file:

- `UI_DICT` — navigation, search form, profile labels, footer (~270 entries)
- `CATEGORY_DICT` — the full forum category tree (~1300 entries)
- `EXTRA_DICT` — subforum names, descriptions and table UI of forum pages
- `TOPIC_DICT` — torrent page, wishlist, messages, search and editor strings
- `PROFILE_DICT` — profile edit form and country list
- `GROUP_DICT` — user group names

Matching is exact, on the whole trimmed string. Anything not in the dictionary is left untouched, which is why torrent and topic titles never need special-casing to stay in Russian.

A few extra rules cover text that mixes a label with dynamic data: Russian month abbreviations, relative durations, and count prefixes like "Search results: 500".

## Found something wrong or missing?

RuTracker has a lot of subforums, and part of the category dictionary was machine-translated, so a handful of the more obscure ones read awkwardly or got missed.

- Open an issue with the string that's wrong or missing.
- Better yet, open a pull request. Both dictionaries are plain JS objects, one entry per line, sorted alphabetically — find the Russian key and fix the English value, or add a new line if it's missing.

If this is useful to you, a star helps other people find it.

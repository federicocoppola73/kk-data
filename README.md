# Kit & Kick — Data

Version-controlled editorial content for the Kit & Kick football quiz game.

## What belongs here
- Player and club records
- Quiz questions and career paths
- Localised content
- Content schemas and validation examples
- Small, properly licensed image assets (if needed during the initial phase)

## Source of truth
This repository is the editorial source of truth for structured content. If content is later published to Firebase/another backend, use a repeatable import/sync process rather than manually maintaining two independent copies.

## Asset policy
- Prefer relative asset paths or stable asset IDs, never hardcoded raw GitHub URLs in app code.
- Record source, licence, attribution and permission status for every third-party image.
- Do not scrape images from Google, social networks or club/player websites.
- Do not assume player photographs, club crests, league marks or sponsor marks are free to use.
- Keep large binary collections out of Git. Move image delivery to object storage/CDN when volume or traffic justifies it.

## Validation
The JSON examples in this repository document the initial data contract. Automated validation and a publishing pipeline will be added before production content is loaded.


## Player ID starter content

- `players/player-id-starter-20.json` contains 20 well-known current and retired players.
- `questions/player-id-starter-20.json` contains one draft photo-identification question per player.
- Question options are omitted intentionally: the app should generate three distractors from the eligible player pool.
- All starter questions are disabled and all portrait rights are pending. Add properly licensed portrait files and record the supporting rights evidence before enabling any question.


## Player portrait assets and attribution

- Portrait files are stored in `players/pending/` and referenced by `players/player-id-starter-20.json`.
- `players/player-image-credits.json` is the source and attribution register for all 20 portraits.
- The register records the Wikimedia Commons source page, creator information, the file-specific licence where confirmed, and review status.
- Licences differ between files. Do not assume the whole collection is covered by one licence.
- All portraits remain pending and are not cleared for production use. Verify missing licence data, attribution, local modifications, and any applicable personality/privacy rights before enabling the questions.


## Club ID starter content

- `clubs/club-id-starter-12.json` contains 12 draft club records for the progressive-clue version of Club ID.
- Clue order: city, founding year, club colours, stadium, nickname.
- The nickname is optional. When it is absent, the game should show four clues and use the four-clue scoring schedule.
- Prototype rules in the dataset: 10 questions per round, four answer options, a 4-second reveal interval and 25 XP per correct answer.
- The starter records include English and Italian values for city and colours. Other UI translations remain managed in `kk-app`.
- Data is marked as draft/partial pending a complete fact-check. Confirm current stadium naming and nickname usage against official club sources before production.


## Stadium ID starter content

- `stadiums/stadium-id-starter-30.json` contains 30 worldwide starter stadium records across England, Spain, Italy, Germany, Brazil and Mexico.
- Each question uses five progressive clues in this order: opening year, capacity, notable event, city and country, home team(s).
- Prototype rules: 10 questions per round, four answer options, 4-second automatic reveal, manual reveal, 200/160/120/80/40 points by clue used, and 25 XP per correct answer.
- Distractor selection is restricted to the same city first, then the same country. Cross-country distractors are not allowed. If three eligible distractors cannot be found, the question must not be served.
- Original illustration paths are planned under `assets/stadiums/illustrations/`; no illustration files are included yet.
- All records are disabled and remain draft. Opening years, capacities, notable events, official stadium names and home-team relationships require primary-source verification before production.
- `schemas/stadium.schema.json` documents the initial dataset contract.

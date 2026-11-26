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

# Archive And Ingestion

Use this reference when the user wants bulk crawling, archive/database storage, duplicate checks, or reuse of existing source records.

## Modes

### Bulk Ingestion Mode

Use when the user asks to crawl or collect many sources automatically.

Behavior:

- Check the archive before researching each candidate.
- If a candidate already exists, skip it silently and record the skip in the log.
- Do not ask the user for decisions on ordinary duplicates, low-value candidates, or routine misses.
- Report only severe issues: broken archive access, repeated source failures, permission problems, schema mismatch, or a high duplicate rate that makes the crawl unproductive.
- Keep a log with counts and reasons.

Minimum log fields:

```text
started_at
query_or_topic
candidates_found
new_records_saved
duplicates_skipped
low_confidence_skipped
errors
notes
```

### User-Specified Mode

Use when the user names a specific song, poem, literary work, film scene, or gives a fixed list.

Behavior:

- Check the archive first.
- If the exact source or a strong alias match already exists, tell the user before redoing work.
- Offer choices: reuse existing record, update it, make a remix/new angle from it, or create a new version anyway.
- If the user gave a list, report which items already exist and continue only with the new ones unless the user asks otherwise.

### Archive Reuse Mode

Use when the user wants to make content from an existing archive during low-budget or no-agent-budget periods.

Behavior:

- Treat every archive record as a bundle of reusable assets, not a single finished post.
- Extract remaining value only when requested: hooks, alternate POVs, unused visual objects, remix styles, shorter edits, lyric captions, cover art variants, duet versions, seasonal variants, or posting plans.
- Prefer low-cost reuse over fresh research unless the archive record lacks essential metadata.
- Do not include a reuse plan, posting calendar, or "what to do next" section in ordinary source or production outputs. Keep reuse notes internal or metadata-only unless the user explicitly asks for lục kho, tái chế, reuse, remix, or lịch đăng.

## Duplicate Key

Use multiple fields, not title alone:

- original title;
- romanization and translated title;
- creator/author/composer/performer;
- source type: song, poem, novel, play, folklore, film scene, historical anecdote;
- year;
- language/country;
- aliases;
- official or canonical URL;
- fingerprint fields if available, such as ISRC, album, film title, poem first line, book chapter, or source collection.

## Source Types

The archive should support both music and non-music inspiration sources:

- song or soundtrack cue;
- film/drama/game theme;
- poem;
- literary excerpt;
- novel or short story;
- folklore/myth/legend;
- historical anecdote;
- theatrical scene;
- visual artwork or cultural object.

For non-song sources, store the emotional engine, central image, speaker position, conflict, and transformable song premise.

## Record Shape

Suggested record fields:

```json
{
  "id": "",
  "source_type": "",
  "canonical_title": "",
  "original_title": "",
  "aliases": [],
  "creators": [],
  "year": "",
  "language": "",
  "country_or_region": "",
  "source_urls": [],
  "confidence": "high|medium|low",
  "origin_context": "",
  "creative_dna": {
    "emotional_engine": "",
    "narrative_pressure": "",
    "speaker_position": "",
    "hook_promise": "",
    "sonic_or_style_signature": "",
    "memory_images": [],
    "audience_use": []
  },
  "do_not_copy": [],
  "new_song_angles": [],
  "visual_anchors": [],
  "reuse_ideas": [],
  "status": "new|used|remixed|archived",
  "created_at": "",
  "updated_at": ""
}
```

## Skip Rules

Skip automatically during bulk ingestion when:

- the source is already in the archive;
- source identity is too ambiguous to resolve cheaply;
- all useful claims are unsourced fan lore;
- the story has no clear emotional engine or visual anchor;
- the source is too legally or culturally risky for the user's intended content.

Do not skip silently in user-specified mode. Report the issue and let the user decide.

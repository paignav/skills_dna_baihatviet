# Bulk Ingestion Prompt

Use Song DNA System in Bulk Ingestion Mode.

Task:

```text
Crawl and collect source records for this topic:
<TOPIC>

Archive location/schema:
<ARCHIVE INFO>

Rules:
- Check duplicates before researching each candidate.
- If already in archive, skip silently.
- Store only new valid source records.
- Include songs, film themes, literature, poetry, folklore, and story sources when relevant.
- Do not create production packs unless requested.
- Do not ask for decisions on ordinary skips.
- Report only severe errors.
- Return only a compact ingestion log.
```

Expected log:

```json
{
  "started_at": "",
  "query_or_topic": "",
  "archive_checked": true,
  "candidates_found": 0,
  "new_records_saved": 0,
  "duplicates_skipped": 0,
  "low_confidence_skipped": 0,
  "errors": [],
  "notes": []
}
```

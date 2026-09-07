# Local Workflow

This repo is designed to be the single local working folder for all AI agents.

Recommended Windows location:

```text
D:\AI_MUSIC\skills_dna_baihatviet
```

Do not use Downloads as the main working location. Keep one stable folder and let GitHub Desktop sync it.

## The Rule

All agents must treat this folder as the central archive.

```text
skills_dna_baihatviet/
  README.md
  LOCAL_WORKFLOW.md
  prompts/
  schemas/
  skills/
  data/
```

No source DNA, production pack, logs, or progress records should be saved outside `data/`.

## Data Folders

| Folder | Purpose |
|---|---|
| `data/sources/` | Source records: songs, poems, film themes, folklore, stories, literary excerpts |
| `data/productions/` | Original production packs developed from source DNA |
| `data/logs/` | Bulk crawl logs, duplicate skips, errors, run summaries |
| `data/indexes/` | Duplicate indexes and lookup files |
| `data/inbox/` | Raw notes, rough lists, URLs, or user-provided source batches waiting to be processed |
| `data/archive/` | Older outputs, retired records, or manual backups |

## Prompt For Any AI Agent

Give this to any AI agent before work:

```text
Work inside this local folder:
D:\AI_MUSIC\skills_dna_baihatviet

Read README.md first.
Read LOCAL_WORKFLOW.md second.
Read prompts/agent_handoff_prompt.md before producing data.

All persistent data must be saved under data/.
Do not save source DNA, lyrics, prompts, visual concepts, narration, logs, or progress files outside data/.

Before researching or processing a new source, check data/indexes/ and existing files in data/sources/.

If mode is bulk ingestion and a duplicate is found, skip it silently and record the skip in data/logs/.
If I explicitly name a source and it already exists, report that it exists and ask whether to reuse, update, remix, or redo.

Respect requested_depth:
source_only, dna_only, song_brief, song_pack, visual_pack, narration_pack, full_production, archive_reuse.

Always save requested_depth, stage, available_blocks, missing_blocks, and next_actions so another agent can continue later.
```

## Common Commands To Give Agents

DNA only:

```text
Use Song DNA System in this folder.
Topic/source: [paste source]
requested_depth: dna_only
Save the source record and progress under data/.
```

Upgrade an existing DNA record:

```text
Use Song DNA System in this folder.
Find existing source record: [title or id]
Upgrade it to requested_depth: song_pack
Save the production pack under data/productions/.
```

Bulk ingestion:

```text
Use Song DNA System in this folder.
Mode: bulk ingestion
Topic: famous cổ phong songs, classic soundtrack themes, poems, folklore, and literary sources suitable for Vietnamese Nhạc Thơ.
requested_depth: dna_only
Skip duplicates silently. Save run log under data/logs/.
```

Visual/copy pack:

```text
Use Song DNA System in this folder.
Find existing source or production: [title or id]
Create requested_depth: visual_pack and narration_pack.
Save outputs under data/productions/.
```

## GitHub Desktop Workflow

After each useful work session:

1. Open this folder in GitHub Desktop.
2. Review changed files.
3. Delete temporary junk files if any.
4. Commit to `main`.
5. Push origin.

GitHub is the backup and transfer copy. The local PC folder is the main working archive.

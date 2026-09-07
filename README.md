# Song DNA System

Portable workflow for turning songs, film themes, poems, folklore, and literary sources into original Vietnamese music production packs.

This repo contains two layers:

- `skills/song-dna-composer/`: Codex skill version.
- `prompts/` + `schemas/`: portable version for other AI agents such as ChatGPT, Claude, Gemini, Antigravity, Hyperframe, or local agents.

## What It Produces

A normal production output should include:

- source/reference DNA;
- original song brief;
- Vietnamese lyric or lyric skeleton;
- Suno/ACE-Step style prompt;
- visual concept for Reels/Shorts;
- narration/copy pack;
- archive metadata.

Vietnamese vocal-fit checks, including cưỡng âm control, run internally by default. Do not output tone-audit tables unless explicitly requested.

## Main Modes

### Reference-To-New-Song

Use when a source is named and the goal is a new song.

Example:

```text
Use Song DNA System. Reference: 弱水三千. Create a Vietnamese cổ phong duet production pack.
```

### Bulk Ingestion

Use when collecting many sources into a data archive.

Rules:

- check duplicate records first;
- silently skip duplicates;
- log counts and errors;
- report only serious issues.

### User-Specified Source

Use when the user gives one source or a fixed list.

Rules:

- check duplicates first;
- if already in archive, report it and let the user decide;
- do not redo automatically.

### Archive Reuse

Use only when explicitly asked to lục kho, tái chế, remix, or make a posting plan from old records.

## Recommended Repo Workflow

```text
1. Give the agent prompts/agent_handoff_prompt.md
2. Require output to match schemas/production_pack.schema.json
3. Save source records using schemas/source_record.schema.json
4. Keep examples/ as behavioral reference
```

## Folder Structure

```text
song-dna-system/
  README.md
  prompts/
    agent_handoff_prompt.md
    bulk_ingestion_prompt.md
    archive_reuse_prompt.md
  schemas/
    source_record.schema.json
    production_pack.schema.json
    ingestion_log.schema.json
  examples/
    ruoshuisanqian.production.md
    ruoshuisanqian.source.json
  skills/
    song-dna-composer/
```

## Notes

This system is for creating original derivative inspiration workflows, not copying protected songs. It should transform at least four layers: setting, relationship, metaphor, hook phrase, genre, vocal perspective, or ending emotion.

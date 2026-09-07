# Completion Stages

Use this reference when the user wants partial outputs, staged production, resume-from-archive behavior, or a specific completion depth.

## Principle

Do not force a full production pack when the user only needs source DNA, a song brief, lyrics, visuals, narration, or archive metadata. Respect the requested completion depth and save progress so later tasks can continue from the current stage.

## Requested Depth

Use `requested_depth` to record what the user asked for in the current run:

- `source_only`: identify and save the source, no DNA.
- `dna_only`: extract source DNA only.
- `song_brief`: create original song premise/title/angle from DNA.
- `song_pack`: create lyrics plus Suno/ACE-Step style prompt.
- `visual_pack`: create visual concept and prompts, with or without lyrics depending on available blocks.
- `narration_pack`: create narration/copy assets, with or without lyrics depending on available blocks.
- `full_production`: create all normal production blocks.
- `archive_reuse`: create only explicitly requested reuse/remix assets.

## Stage

Use `stage` to record the highest completed state:

- `source_found`
- `dna_extracted`
- `song_brief_created`
- `lyric_draft_created`
- `music_prompt_created`
- `visual_pack_created`
- `narration_pack_created`
- `ready_to_produce`
- `published_or_archived`

Stages are not always strictly linear. For example, a user may request a visual pack directly from DNA before lyrics exist. In that case, keep `stage` at the highest meaningful completed state and use `available_blocks` / `missing_blocks` for precision.

## Blocks

Track progress with:

- `available_blocks`: blocks already created and usable;
- `missing_blocks`: blocks not created yet;
- `next_actions`: reasonable next steps from the current state.

Common blocks:

- `source_identity`
- `source_dna`
- `original_song_brief`
- `lyric_pack`
- `music_prompt`
- `visual_pack`
- `narration_copy`
- `archive_metadata`
- `publish_metadata`

## Behavior

- Stop at the requested depth.
- Do not generate lyrics, visual prompts, narration, or reuse plans unless requested or required by the selected depth.
- If continuing an existing record, read `stage`, `available_blocks`, and `missing_blocks` first.
- If the existing record already satisfies the requested depth, report that it is already available and ask whether to reuse, revise, or expand.
- In bulk ingestion mode, default to `dna_only` unless the user requests a deeper level.
- In user-specified mode, default to `full_production` only when the user asks to create a complete song/content pack.

## Minimal Stage Outputs

### dna_only

Return or save:

- source identity;
- source confidence;
- creative DNA;
- do-not-copy list;
- stage metadata.

Do not generate lyrics, music prompts, visuals, narration, or reuse plans.

### song_brief

Return or save:

- DNA summary;
- three original directions;
- chosen or recommended direction;
- title options;
- premise, characters, setting, message;
- stage metadata.

### song_pack

Return or save:

- song brief;
- lyric pack;
- music prompt;
- internal vocal-fit check already applied;
- stage metadata.

### full_production

Return or save:

- song brief;
- lyric pack;
- music prompt;
- visual pack;
- narration/copy pack;
- archive metadata;
- stage metadata.

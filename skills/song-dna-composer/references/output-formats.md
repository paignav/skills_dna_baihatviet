# Output Formats

Use these templates as starting points, not rigid forms.

## Reference-To-New-Song Brief

```markdown
Reference:
Tên gốc:
Năm:
Tác giả/nhạc sĩ:
Người thể hiện nổi bật:
Phim/album/sự kiện:

Vì sao đáng học:

DNA có thể chuyển hóa:
- Emotional engine:
- Narrative pressure:
- Hook promise:
- Sonic signature:
- Memory image:
- Audience use:

Không được copy:

Ba hướng bài mới:
1.
2.
3.

Hướng chọn:

Structure map:
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Post-Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]

Hook candidates:

Lyric constraints:

Style of Music:

Visual Reel/Short concept:
- Art concept:
- Key visual:
- Character/costume:
- Location:
- Symbolic object:
- Color palette:
- Image prompt:
- Clip shot list:

Narration/Copy pack:
- Cold open:
- Voice-over 15s:
- On-screen text:
- Caption short:
- Podcast intro:

Nguồn/confidence:

Stage:
- requested_depth:
- stage:
- available_blocks:
- missing_blocks:
- next_actions:
```

## Candidate Discovery For New Songs

```markdown
| Source | Loại | DNA đáng học | Gợi ý bài mới | Điểm sáng tác | Copy-risk |
|---|---|---|---|---:|---|
```

After the table, recommend the top one to three choices and explain which reference should be used first.

## Original Song Starter

```markdown
Tên bài đề xuất:

Premise:

Nhân vật/bối cảnh:

Hook chính:

Structure:

Lyric skeleton:

Style of Music:

Reel visual angle:

Image prompt:

Clip prompts:

Narration/Copy:
- Cold open:
- Voice-over:
- On-screen text:
- Caption:
- Podcast intro:

Nguồn cảm hứng đã biến đổi:
```

## Origin-Only Brief

Use only when the user asks for research without creating a new song.

```markdown
Tên bài:
Tóm tắt:
Bối cảnh ra đời:
Nguồn cảm hứng:
Độ chắc:
Nguồn:
```

## Bulk Ingestion Log

Use for bulk crawling mode. Keep it short unless there are severe errors.

```markdown
Topic/query:
Archive checked:
Candidates found:
New records saved:
Duplicates skipped:
Low-confidence skipped:
Errors:
Notes:
```

## DNA Only Output

Use when the user asks only for DNA/source extraction.

```markdown
Source:
Type:
Confidence:

Creative DNA:
- Emotional engine:
- Narrative pressure:
- Speaker position:
- Hook promise:
- Sonic/style signature:
- Memory images:
- Audience use:

Do not copy:

Stage:
- requested_depth: dna_only
- stage: dna_extracted
- available_blocks:
- missing_blocks:
- next_actions:
```

## Duplicate Report For User-Specified Mode

Use when the user named a specific source or gave a fixed list and one or more items already exist in the archive.

```markdown
Đã có trong kho:
- Source:
- Matched by:
- Existing status:

Bạn muốn:
- reuse existing record
- update existing record
- create remix/new angle
- redo anyway
```

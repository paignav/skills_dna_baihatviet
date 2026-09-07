# Song DNA System

Portable workflow for turning songs, film themes, poems, folklore, and literary sources into original Vietnamese music production packs.

This repo contains two layers:

- `skills/song-dna-composer/`: Codex skill version.
- `prompts/` + `schemas/`: portable version for other AI agents such as ChatGPT, Claude, Gemini, Antigravity, Hyperframe, or local agents.
- `data/`: the single local archive where all agents should save sources, production packs, logs, indexes, and progress.

For local PC usage, read `LOCAL_WORKFLOW.md`. Treat the local folder as the main archive and GitHub as backup/sync.

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

## Hướng Dẫn Nhanh Cho Chính Tôi

Repo này dùng để biến một **nguồn cảm hứng** thành một **gói sản xuất nhạc/content**.

Nguồn cảm hứng có thể là:

- bài hát nổi tiếng;
- nhạc phim;
- thơ;
- truyện;
- điển cố;
- folklore/truyền thuyết;
- cảnh phim;
- giai thoại lịch sử.

Khi dùng với AI agent khác, đưa cho nó file:

```text
prompts/agent_handoff_prompt.md
```

Nếu muốn nó xuất JSON có cấu trúc, bảo nó tuân theo:

```text
schemas/source_record.schema.json
schemas/production_pack.schema.json
schemas/ingestion_log.schema.json
```

Nếu agent hỗ trợ Codex skill, copy thư mục:

```text
skills/song-dna-composer/
```

## Local Data Là Kho Chính

Đặt repo ở một folder cố định trên PC, ví dụ:

```text
D:\AI_MUSIC\skills_dna_baihatviet
```

Mọi AI agent khác phải làm việc trực tiếp trong folder này. Không lưu DNA, lyric, visual concept, narration, log hoặc tiến độ ra chỗ khác.

Kho data nằm ở:

```text
data/
  sources/
  productions/
  logs/
  indexes/
  inbox/
  archive/
```

Luôn đưa cho agent các file:

```text
LOCAL_WORKFLOW.md
prompts/agent_handoff_prompt.md
```

## Mức Độ Hoàn Thiện

Không phải lúc nào cũng cần full pack. Dùng `requested_depth` để nói agent làm đến đâu thì dừng.

| requested_depth | Dùng khi nào | Output chính |
|---|---|---|
| `source_only` | Chỉ muốn lưu nguồn | tên, tác giả, link, metadata |
| `dna_only` | Chỉ muốn lấy DNA, chưa cần lyric | emotional engine, hook promise, memory image, do-not-copy |
| `song_brief` | Muốn ý tưởng bài mới | tên bài, premise, nhân vật, bối cảnh, thông điệp |
| `song_pack` | Muốn đem qua Suno | lyric + style prompt |
| `visual_pack` | Muốn ảnh/clip trước | art concept, image prompt, shot list |
| `narration_pack` | Muốn lời dẫn/caption/podcast | cold open, voice-over, on-screen text, caption |
| `full_production` | Muốn đủ bộ | lyric, style, visual, narration, metadata |
| `archive_reuse` | Muốn lục kho/tái chế | chỉ tạo phần reuse/remix được yêu cầu |

Ví dụ:

```text
Use Song DNA System.
Reference: 弱水三千.
requested_depth: dna_only.
Chỉ lấy DNA và lưu stage, chưa viết lyric.
```

```text
Use Song DNA System.
Lấy record src_song_ruoshuisanqian_shitou_zhangxiaotang.
Nâng từ dna_only lên song_pack.
```

```text
Use Song DNA System.
Topic: cổ phong Trung có thể Việt hóa thành Nhạc Thơ.
Mode: bulk ingestion.
requested_depth: dna_only.
Skip nguồn đã có trong kho, chỉ trả ingestion log.
```

## Stage Và Resume

`stage` là tiến độ thật của record. `requested_depth` là mức yêu cầu trong lần chạy hiện tại.

Các stage chính:

```text
source_found
dna_extracted
song_brief_created
lyric_draft_created
music_prompt_created
visual_pack_created
narration_pack_created
ready_to_produce
published_or_archived
```

Mỗi record nên có:

```json
{
  "requested_depth": "dna_only",
  "stage": "dna_extracted",
  "available_blocks": ["source_identity", "source_dna", "archive_metadata"],
  "missing_blocks": ["original_song_brief", "lyric_pack", "music_prompt", "visual_pack", "narration_copy"],
  "next_actions": ["create_song_brief", "create_song_pack", "create_full_production"]
}
```

Lần sau chỉ cần bảo agent nâng stage, không cần cào lại từ đầu.

## Quy Tắc Kho Data

Bulk mode:

- check kho trước;
- gặp trùng thì skip im lặng;
- chỉ ghi log;
- không báo cáo từng bài nếu không lỗi nặng.

User-specified mode:

- nếu tôi chỉ đích danh một bài/tác phẩm mà kho đã có, phải báo;
- hỏi tôi muốn reuse, update, remix/new angle hay redo;
- không tự làm lại.

Vocal-fit/cưỡng âm:

- luôn chạy ngầm khi tạo lyric tiếng Việt;
- không xuất bảng kiểm tra;
- không lưu bảng kiểm tra vào kho;
- chỉ báo khi tôi yêu cầu kiểm tra ngữ âm/cưỡng âm hoặc có lỗi nghiêm trọng.

Reuse plan:

- không xuất mặc định;
- chỉ xuất khi tôi hỏi lục kho/tái chế/remix/lịch đăng.

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
  data/
    README.md
    sources/
    productions/
    logs/
    indexes/
    inbox/
    archive/
  examples/
    ruoshuisanqian.production.md
    ruoshuisanqian.source.json
  skills/
    song-dna-composer/
```

## Notes

This system is for creating original derivative inspiration workflows, not copying protected songs. It should transform at least four layers: setting, relationship, metaphor, hook phrase, genre, vocal perspective, or ending emotion.

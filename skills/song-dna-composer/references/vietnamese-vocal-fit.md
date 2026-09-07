# Vietnamese Vocal Fit

Use this reference whenever drafting or revising Vietnamese lyrics for a singing model such as Suno or ACE-Step. The goal is not academic tone analysis; it is preventing awkward, forced, or hard-to-sing Vietnamese.

## Main Risk: Cuong Am

Avoid placing words with dau nang or dau nga at likely high, long, or strongly emphasized positions:

- final word of a chorus line;
- title hook;
- pre-chorus lift;
- last word before a rest;
- melismatic or ad-lib position;
- repeated post-chorus chant.

Prefer open, singable tones for those positions:

- thanh ngang: ta, xa, mưa, hoa, trôi;
- thanh sắc when a bright lift is useful: nhớ, tới, sáng;
- soft thanh huyền for falling resolution: đời, người, chiều.

Use nang/nga in lower, shorter, passing positions when needed for meaning, but avoid stacking many of them in a single hook.

## Syllable Mapping

For repeated sections, keep matching lines close in length. A useful default:

- verse lines: usually 5-8 syllables;
- pre-chorus lines: usually 6-9 syllables;
- chorus hook lines: usually 4-7 syllables;
- post-chorus chant: 2-5 syllables.

When revising an existing lyric, preserve the original phrase length unless there is a clear reason to simplify. A tolerance of one syllable is usually acceptable.

Count Vietnamese syllables by written word units. Hyphenated or foreign words may be ambiguous; rewrite them if Suno may misread them.

## Breath And Punctuation

Use punctuation as singing guidance:

- comma for a short breath;
- ellipsis for a held pause or emotional drag;
- line break for phrase reset;
- avoid long unpunctuated lines in chorus.

Write numbers as words to avoid text-to-speech reading errors.

## Revision Output

Run vocal-fit checks internally by default. Do not include cuong-am tables, syllable notes, or tone-by-tone explanations in normal deliverables or archive records.

Only include a short audit table when:

- the user explicitly asks for cuong-am, ngữ âm, syllable, or singing-difficulty analysis;
- the user asks why a line was changed;
- a serious unresolved singing issue remains and needs a decision.

```markdown
| Dòng gốc | Vấn đề hát | Dòng sửa |
|---|---|---|
```

Focus on lines with real singing risk. Do not over-audit harmless lines.

## Practical Heuristics

Good hook ending words:

- thôi, rồi, xa, qua, trôi, bay, mưa, hoa, người, đời, thương, nhớ.

Risky hook ending words:

- một, gặp, nợ, cũ, giữ, lỡ, vẫn, mãi, chẳng, vỡ, khóc, tiếc.

Risky words can still work in short notes. They become a problem when stretched, repeated, or placed at the emotional peak.

## Suno/ACE-Step Notes

For lyrics intended for AI music generation:

- Put the cleanest hook in the chorus, not only in the prompt.
- Avoid overloading each line with Sino-Vietnamese words.
- Favor concrete images over abstract moral statements.
- In style prompts, request "singable Vietnamese phrasing" and "clear vocal diction"; do not rely on the prompt to fix bad lyrics.

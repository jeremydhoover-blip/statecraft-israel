# Video script skill (version 0.2, draft, proposed in #639)

A starter for a `statecraft-video-script` skill: the style, tone, voice, language, terminology, storytelling and sourcing rules for video scripts and narration, written so that a script does not have to be invented from nothing each time and does not read like a generic AI script.

Status: version 0.2, draft. Published as a folder on a fork branch, linked from issue #639. The maintainer has answered the location, order and AI narrator questions (below). The trailer quote source sheet goes first as its own small PR, and this skill follows it into `.github/skills/statecraft-video-script/`.

## Decisions from the maintainer (#639, 15 October 2026)

- Location: `.github/skills/statecraft-video-script/`, beside `statecraft-writing-voice`.
- Order: the trailer quote source sheet first (source URL, date, verbatim, excerpt or paraphrase, translator for English and Hebrew), then this skill.
- An AI narrator is allowed. It speaks in its own voice, it is disclosed, and it never speaks as a real person.
- Narration and captions are in English and Hebrew. A native reviewer finalises the Hebrew (#564).
- The real script to test against is promo 3, "The Long Way South": an ElevenLabs premade voice, with on-screen captions and decision cards that the voice does not speak.

## What changed from version 0.1

- `references/06-ai-voice-music-and-disclosure.md`: the narrator question is answered; the open questions are now two.
- `examples/case-study-before-after.md`: a new section says what the finished video carries in captions and cards, so the voice-only diagnosis is not read as a verdict on the whole video.
- Line endings are LF.

## What is here

```
statecraft-video-script/
  SKILL.md                       entry point, rules that do not bend, workflow
  references/
    01-audience-and-purpose.md   what the project says about itself, working audience segments
    02-voice-tone-style.md       the narrator, spoken rules, before and after, sensitive subjects
    03-language-terminology.md   dates, money, names, terms, Hebrew, pronunciation
    04-storytelling.md           situation, decision, cost; beat sheet; shapes; endings
    05-claims-quotes-and-sources.md  fact sheet, quote classes, real people
    06-ai-voice-music-and-disclosure.md  what the repo says, proposed voice rules
    07-captions-accessibility-hebrew.md  WCAG 1.2.2 and 1.2.5, Steam, native Hebrew
    08-channels-and-formats.md   Steam, GitHub hero, site, clips, social (open)
  templates/                     brief, shot table, fact sheet, quote sheet, voice brief, pronunciation list, review checklist
  scripts/check_script.py        lint for a shot-table script (tested on a good and a bad sample)
  prompts/                       draft and review prompts for an AI assistant
  examples/
    example-46s-one-decision.md  worked example that uses only repo-sourced claims (passes the checker)
    case-study-before-after.md   a vague script, why it fails, and a self-contained rewrite (rewrite passes the checker)
```

## How it was grounded

- The project's own rules: `docs/WRITING_GUIDE.md`, `docs/CONTENT_POLICY.md`, the `statecraft-writing-voice` skill, `docs/event-videos.md`, `docs/RELEASING.md`, `docs/steam/*`, `docs/oss/DECISIONS.md`, `README.md`.
- Platform sources opened on 15 October 2026: Steamworks "Trailers", WCAG 2.2 Understanding 1.2.2 and 1.2.5.
- Tags in the files: [V] already a repo rule or opened and read, [H] proposal, [A] assumption to test, [Q] question for the maintainer.

## What is deliberately not decided here

- The audience segments are hypotheses. The repo does not define its audiences.
- Spoken pace (150 wpm), the 18-word sentence flag and the caption line length are assumptions to replace with measured values.
- The AI voice rules are proposals. The repo has no voice policy.
- Social channels and lengths are unknown.
- Pronunciation is left empty on purpose for a native speaker.

## Rules added from a real script

A real narrated script was run through the draft. The maintainers' feedback was: too vague, not informative enough, not enough story, and lines that assume the viewer knows the situation. That became two rules (a cold viewer can follow it; it is a story, not a topic), new checker tests (vague phrasing, ambiguous first references, lines with no concrete detail, silent gaps, empty cues), and the case study.

## Known gaps before this could be a PR

1. More real scripts from the existing narrated videos. One has been tested; the rest are not in the repo. Each real script should be run through the checker and the cold-viewer test, and the rules adjusted.
2. The maintainer's answer on the audience segments and on voice inside the game itself. The other questions in #639 are answered (see above).
3. A native Hebrew reviewer for the Hebrew rules and the pronunciation list.
4. The trailer's quote source sheet (the first worked case for `templates/quote-source-sheet.md`).
5. Add a CHANGELOG line only if the maintainer wants one for a skill under `.github/`, and run `uv run scripts/oss/check_repo.py` and `uv run scripts/oss/md_links.py` on the PR branch.

## Where it lives

`.github/skills/statecraft-video-script/`, as the maintainer decided in #639.

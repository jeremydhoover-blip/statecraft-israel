# 06 AI voice, music and disclosure

Status: DRAFT. Tags: [V] already in the repo, [H] proposal, [Q] question for the maintainer.

## What the repo says today

- Every AI-generated asset has an `ASSETS.yaml` row with `ai_generated: true`, and `docs/ai-disclosure.md` is generated from those rows (#176, `scripts/oss/ai_disclosure.py`). [V]
- The AI clips, images and the cinematic trailer are all listed there, with the tool, the model, the date and a sha256 for files that are not in the repository. [V]
- ElevenLabs Music is licensed for commercial use, owner decision D-M (13 October 2026). It covers the promo cues and marketing. [V, `docs/oss/DECISIONS.md`]
- The Steam draft has a disclosure line for a cinematic teaser "made with AI video, voice and music tools", and the Coming Soon kit says the game has no voice-over. [V, `docs/steam/store-page-draft.md`, `docs/steam/coming-soon-kit.md`]
- The only audio in the game is the archival 1948 recording of Ben-Gurion on the start screen, behind a "Play the recording" button. [V]
- Nothing in the repo governs who or what a synthetic voice may speak as. That is the gap this file proposes to fill.

## Proposed rules [H]

1. **A synthetic voice never speaks as a real, named person.** No cloned voice, no sound-alike, no "voice of" a historical figure, living or dead. A narrator speaks as the project.
2. **Real recordings come from archives**, with the archive, date and rights recorded, as for the Declaration recording.
3. **The narrator is disclosed.** The video description, the caption under any embed and the `ASSETS.yaml` row say the voice is synthetic, and name the tool.
4. **Record how it was made.** Tool, voice id or preset, model, date, the exact script text, the pronunciation list used, the licence or terms, and the sha256 of the file. Large files may stay out of the repo if the hash is recorded, as other promo files do.
5. **No synthetic Hebrew voice until a native reviewer has approved a sample.** The same reviewer signs off the Hebrew captions.
6. **Pronunciation is checked** against the signed-off list before release (`templates/pronunciation-list.md`).
7. **Music** is licensed and recorded in the same way. It never starts before the first fact and never swells on a casualty.
8. **Keep the policy text in step.** If a video adds synthetic voice or music, the README AI-use section, the Steam draft and `docs/ai-disclosure.md` change in the same PR.
9. **Do not generate a voice of a real person to read a quote.** Show the quote as text with its source.

## Questions for the maintainer [Q]

- Is an AI narrator allowed at all? If yes, which tools and which terms apply to voice, as D-M does for music?
- Is voice allowed in the game itself, or only in promotional video?
- Who signs off a Hebrew voice?

## What goes in the `ASSETS.yaml` row

Follow the fields of the existing AI rows (tool, model, date, source path or "not in the repository", sha256, notes, status). Add the voice id or preset and the script hash. Status stays `owner-verify` until the owner records a decision, as for the other AI assets.

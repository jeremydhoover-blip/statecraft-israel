# Case study: from a vague water story to a self-contained one

An existing narrated promo video about water was used to test these rules. The findings are about the text, not about anyone. The point of the case study is the pattern: a script that sounds like a story but assumes the viewer already knows the situation.

## The original (voice-over and cues as supplied)

> [00:01 to 00:24] The young Jewish state faced many problems. One of the most pressing was water. The lake was in the north. The thirst was everywhere else. Negba, 1948. The Egyptian army pushed north. Shells tore through the water tower, but Negba held.
>
> [00:41 to 00:43] In the camps, families waited their turn.
>
> [01:10 to 01:14] A lake carried south, then one drop at a time.
>
> [01:14 to 01:16] Water became a basis for peace.
>
> [01:16 to 01:18] When the rain ran short, we turned to the sea.
>
> [01:41] Thank you.

The checker's verdict on this text: 2 errors and 25 warnings (a line with a date and no source, an empty row, five vague-phrasing hits, four ambiguous first references, 25-second and 23-second gaps, lines with no concrete detail, and a hook that fails with the sound off).

## What the maintainers' feedback was

Too vague. Not informative enough. Not enough story. Lines like "the lake was in the north, the thirst was everywhere else" assume the viewer already knows the situation, and the project cannot assume that.

That feedback is now a rule: **explain first, then evoke** (`references/02-voice-tone-style.md`), and a script must pass the **cold-viewer test**.

## Diagnosis

| Id | The line | Why it fails for a cold viewer | Rule |
|---|---|---|---|
| D1 | "The young Jewish state faced many problems. One of the most pressing was water." | Generic opener. "Many" and "one of the most" give no scale. Nothing is learned. | Say what, how much, where, when. |
| D2 | "The lake was in the north. The thirst was everywhere else." | Which lake? Which north? Whose thirst, and where? A contrast line that works only if the viewer already knows the geography. It also overclaims ("everywhere"). | Explain first, then evoke. Name the place and give the plain fact the line compresses. |
| D3 | "Negba, 1948. The Egyptian army pushed north. Shells tore through the water tower, but Negba held." | Specific, but disconnected: what is Negba, why does its water tower matter here? The wording is stronger than the sources found (a kibbutz whose water tower still carries bullet holes from the 1948 fighting [S]). "Held" needs its own source. | One sentence that ties the event to the story, worded no more strongly than the source, or cut. |
| D4 | "In the camps, families waited their turn." | Which camps? Waiting for what? No source. | Define on first mention, with a source. |
| D5 | "A lake carried south, then one drop at a time." | Two separate developments compressed into a metaphor, neither named, neither dated. | Name the thing, give the date, then the image. |
| D6 | "Water became a basis for peace." | A slogan. Which peace, what water, how much? A loaded claim needs a source and care. | Name the agreement, the year, the amount. |
| D7 | "When the rain ran short, we turned to the sea." | Who is "we"? Desalination is never named. No date or scale. | Name it, date it, give a number. Keep the narrator's person consistent. |
| D8 | "Thank you." | Not a next step. | Verb plus a place that exists today. |
| D9 | The whole script | No premise (what is the viewer watching?), no decision, no consequence. The footage shows a real decision card that the voice never mentions. Gaps of 25 and 23 seconds and a 10-second paragraph mark with no content. Cues of 10 words in 2 seconds cannot be spoken, so the file is a caption list, not a script. | Use the shot table. One story with a setting, a problem, a decision and a result. Picture and voice tell the same story. |

## What works and should be kept

- Concrete images. A real archival photograph shown first, credited.
- Short sentences.
- The theme. Water scarcity is a good fit for the game's own idea that every choice is paid for somewhere else.
- "One drop at a time" is a good line once the viewer knows what it refers to.

## A rewritten version

A rewrite that keeps the images and the theme, and is self-contained. It is a draft for a team to verify, not a finished script: every [S] needs a primary source and the [GAP] needs finding before it is recorded.

```
Title: Water, a story in four decisions (draft rewrite)
Channel: social, Steam or site (to decide)
Length (seconds): 73
Language: en
Audience: strategy players (primary), history-minded players (secondary)
Build id or footage note: REPLACE with a real build and commit id. The 2002 card is not on upstream/main.
```

| # | Time | Picture | On-screen text | Voice-over | Sources |
|---|---|---|---|---|---|
| 1 | 0-6 | Real build: the Hula card, 1951 | 1951. The prime minister must decide whether to keep draining the Hula swamps, near the Syrian border. | In 1951, Israel's prime minister must decide whether to keep draining the Hula swamps. | F1, game:G1 |
| 2 | 6-17 | Map pan: north to south | Water: northern Israel. People: central Israel. Desert: southern Israel. | The Sea of Galilee, a freshwater lake, is in northern Israel. Central Israel is the most populated part of the country, and southern Israel is arid. | F2 |
| 3 | 17-31 | Archival photograph of the Carrier, or an illustration labelled "AI-generated illustration" | 1964. The National Water Carrier. About 130 km of pipes, canals and tunnels. | In 1964 Israel finished the National Water Carrier. It moves water from the Sea of Galilee to central and southern Israel. The route is about 130 kilometres of pipes, canals and tunnels. | F3 |
| 4 | 31-43 | Title graphic | 1994. Israel agrees to send Jordan 50 million cubic metres of water a year. | Water is also part of Israel's peace with Jordan. Under the 1994 peace treaty, Israel agreed to send Jordan 50 million cubic metres of water a year. | F4 |
| 5 | 43-55 | The 2002 card, labelled "in development, not in the current build" | 2002. After a long drought, a first large seawater plant is tendered. | After a long drought, Israel tenders its first large seawater desalination plant. By 2015, roughly half of its drinking water came from desalination. | game:G5, F5, F6 |
| 6 | 55-63 | The card's two options | Make desalination a main source, or keep it small and cut farm water quotas. | In 2002 you choose: make desalination a main source, or keep it small and cut farm quotas. | game:G5 |
| 7 | 63-73 | The Why panel, then the title card | Each choice costs something elsewhere. Statecraft: Israel. Free and open source. Every fact has a source. github.com/eyalgolan/statecraft-israel | Each choice costs something elsewhere, and the Why panel shows what. Statecraft: Israel is free and open source, and every fact has a source. | game:G3, F7 |

### Fact sheet for the rewrite

| Id | Claim | Kind | Source | Tag |
|---|---|---|---|---|
| F1 | In 1951 drainage works south of Lake Hula reached the demilitarised zone with Syria, and the drainage of the Hula swamps was reported by JTA. | history | `content/events/hula_drainage.yaml` and its sources (FRUS 1951 vol V doc 288, JTA) | [V] in the project's content file |
| F2 | The Sea of Galilee is a freshwater lake in the north. The Carrier moves its water to the highly populated centre and the arid south. | history | en.wikipedia "National Water Carrier of Israel", lead and route sections, opened 15 Oct 2026. Find a primary source (Mekorot, the Water Authority). | [S] |
| F3 | The National Water Carrier was completed in 1964, is about 130 km long, and is made of giant pipes, open canals, tunnels, reservoirs and pumping stations. | history | same page | [S] |
| F4 | Under the 1994 Israel-Jordan treaty, Israel agreed to transfer 50 million cubic metres of water a year to Jordan. | history | same page, citing the treaty. Read the treaty annex. | [S] |
| F5 | By 2015 about half of Israel's drinking water came from desalination (35% in 2014 on the same page). | history | en.wikipedia "Desalination by country", Israel section, opened 15 Oct 2026, citing AP and the New York Times. Find the Water Authority figure. | [S] |
| F6 | When, and where, Israel tendered its first large seawater plant. | history | not found | [GAP] |
| F7 | The game is free and open source; every fact carries a source; the repository address. | game | `README.md`, `site/public/media/promo-trailer.en.vtt` | [V] |
| G1 | The Hula decision card is in the build. | game | `content/events/hula_drainage.yaml` | [V] |
| G3 | The Why panel explains a turn's changes. | game | `README.md` | [V] |
| G5 | A 2002 card, "Desalinating the Sea", with two options. | game | not on `upstream/main` on 15 Oct 2026. Confirm its status and sources with the maintainer. | unreleased |

### Notes on the rewrite

- The through-line is the game's own idea: scarcity forces choices that cost something elsewhere. Each beat is one choice or consequence the viewer can understand without background.
- Negba is not in the rewrite. If it comes back, it needs the sentence that links it to the story and wording no stronger than the source: "Negba's water tower, still standing, carries bullet holes from the 1948 fighting [S]."
- A viewer will see the card on screen and hear what it says. The original's strongest asset, a real decision card, is now the story.
- Anything in the 2002 beat is for a later era. It must be labelled "in development" and must not be shown as playable.

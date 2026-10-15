# Example: 46 seconds, one real decision

A worked example. It tells one real decision from the game in plain words, so a viewer who has never heard of the period understands what happened and what the choice is. Every claim about the game or the history points at a source id. It is a teaching example, not a script to publish: the footage and build id are placeholders.

```
Title: Example 46 second one-decision explainer
Channel: social (example only)
Length (seconds): 46
Language: en
Audience: strategy players (primary), history-minded players (secondary)
Build id or footage note: REPLACE with a real build and commit id
```

## Shot table

| # | Time | Picture | On-screen text | Voice-over | Sources |
|---|---|---|---|---|---|
| 1 | 0-5 | Real build: the Hula decision card | 1951. Israel's prime minister must decide. | It is 1951, and Israel's prime minister has a decision to make. | F1, game:G1 |
| 2 | 5-14 | Real build: map pan to northern Israel, then the card text | Drainage works near Lake Hula have reached a demilitarised zone on the Syrian border. | Israeli drainage works near Lake Hula, in northern Israel, have reached a demilitarised zone on the Syrian border. | F1, F2 |
| 3 | 14-22 | Card text | Syria has complained. The armistice commission's chairman asks Israel to stop. | Syria has complained. The armistice commission's chairman asks Israel to stop work until there is an agreement. | F1, F3 |
| 4 | 22-30 | Card options | Continue the works. Or halt until there is agreement. | You can continue and assert Israel's rights in the zone, or halt until there is agreement. | game:G2 |
| 5 | 30-40 | The top bar before and after, then the Why panel | Continue: security up, international standing down. Halt: the reverse. | Continue, and security rises but international standing falls. Halt, and it goes the other way. The Why panel shows what caused each change. | game:G3, game:G4 |
| 6 | 40-46 | Title card | Statecraft: Israel. Free and open source. A source for every fact. | Statecraft: Israel is free and open source, and every fact has a source. | F4 |

## Fact sheet for this example

| Id | Claim | Kind | Source | Tag |
|---|---|---|---|---|
| F1 | In 1951, drainage works south of Lake Hula, under the Palestine Land Development Company's concession, reached the demilitarised zone with Syria. | history | `content/events/hula_drainage.yaml` (event window 7 March to 18 May 1951), citing FRUS 1951 vol V doc 288 and a JTA report, checked 2026-10-10 by the maintainer | [V] in the project's content file, not re-opened for this example |
| F2 | Lake Hula is in the north of Israel. | history | Confirm on the in-game map and in one reference | [S] |
| F3 | Syria complained, and the chairman of the armistice commission asked that work stop pending agreement. | history | Same event file and the same sources as F1 | [V] in the project's content file |
| F4 | The game is free and open source and every historical fact carries a source. | game | `README.md` tagline | [V] |
| G1 | The Hula decision card appears in the build for the prime minister. | game | `content/events/hula_drainage.yaml`; confirm in the recorded build | [V] |
| G2 | The two options are "Continue the works and assert Israel's rights in the zone" and "Halt the works until there is agreement". | game | same file | [V] |
| G3 | The Why panel explains a turn's changes. | game | `README.md`, "What it looks like today" | [V] |
| G4 | Continuing raises security and lowers international standing. Halting lowers security and raises international standing. | game | the options' effects in the same event file; confirm the numbers in the recorded build | [V] |

## What this example shows

- A viewer who knows nothing learns who (Israel's prime minister), when (1951), where (near Lake Hula, on the Syrian border), what (drainage works reached a demilitarised zone), the problem (Syria complained and the commission's chairman asked Israel to stop) and the choice, with what each option costs.
- Every line works with the sound off. The on-screen text carries the message.
- No adjective carries a claim. The "cost somewhere else" idea arrives as a visible trade-off in the top bar, not as a slogan.
- Picture and voice tell the same story: the card on screen is the decision the voice describes.

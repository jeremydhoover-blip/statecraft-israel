# Hebrew localisation guide for Statecraft: Israel (draft v0.2)

Status: DRAFT for discussion. Not approved by the maintainer. **No rule here is final until a native Hebrew reviewer has signed it off.** Hebrew in this draft has been reviewed by a non-native reader and not finalised.
Date: 15 October 2026. Evidence date: strings snapshot of `upstream/main` 50ba5d5c, 15 October 2026 (218 keys in each language).

This guide covers how Hebrew is written and displayed in the game and its surfaces. It builds on the English UI microcopy guide and the glossary. It does not cover event card prose, which exists in English only today (HE-12).

## How to use this guide

- A writer or translator reads the rules and the checklist.
- A native reviewer works through the "For the native reviewer" lists, decides each open point, and signs off by name and date (HE-14).
- An AI agent reads the agent brief first. It must never finalise Hebrew and must flag every Hebrew string for native review.
- Every quoted string is a real string from `strings.he.yaml` or `strings.en.yaml`, or a real line from the sources named. Rewrites are labelled "candidate".

Rule status legend: **observed** (already the practice), **proposed** (new), **maintainer** (needs Eyal's decision), **native** (needs a native Hebrew reviewer), **code** (needs a code change).

## Where the Hebrew stands today (checked facts)

- `strings.he.yaml` has 218 keys, the same keys and placeholders as `strings.en.yaml`, and repo tests enforce this (HE-01). The game loads the Hebrew strings only when Hebrew is asked for by hand: `?lang=he` on the web and `-lang he` on the desktop, with no visible switch yet (the file header; #193, #506). Eyal's 13 October status on #193 said the Hebrew font and right-to-left layout exist.
- Each text takes its direction from its own first letter, and a repo test checks it. The same test notes that the date is still English (#55).
- Dates, money, names and content still arrive in English from the simulation's formatter, so a Hebrew line can contain "15 May 1948" or "IL 18.6m" (the file header says so). One part is now localised: the twelve month names and two date patterns exist in Hebrew (`date.*`, used by the map's control captions).
- Since #543 `UiText.Format` puts an invisible left-to-right mark (U+200E) on both sides of each value it inserts into a Hebrew pattern, unless the value already contains Hebrew. An English date, an amount or a minus sign then reads as one run.
- Event text and unit text are English only. Whether to localise content is open (#55). Since #558 the content files carry sourced Hebrew names for offices (with feminine forms where a woman held the office), parties, governments, legislatures and places. By `git grep`, Unity scripts read only the places' Hebrew names so far.

## Agent brief

Use when writing or reviewing Hebrew for Statecraft: Israel. Never present a proposal as an approved rule. Never finalise Hebrew; flag it for a native reviewer.

1. Hebrew mirrors English key for key, with the same placeholders (HE-01).
2. One Hebrew word per concept, from the glossary. Do not introduce a second word for a concept already in use (HE-02).
3. Do not use the masculine imperative or slash forms. Prefer an action noun, "יש ל...", a word ending in ך or ת, or a neutral first person (HE-03).
4. Write counts as "Label: N". Do not build sentences whose wording changes with the number (HE-04).
5. Full spelling (ktiv male) for modern text (HE-05).
6. Punctuation is ASCII, as in English. Acronyms take gershayim before the last letter. Pick one gershayim character and use it everywhere (HE-06).
7. A prefix before a numeral or Latin letters takes a maqaf, per the Academy (HE-07).
8. Digits are Latin. Do not type dates or money into a string. Month names come from the `date.*` keys; money is not yet localised (HE-08).
9. Inserted values are wrapped in direction marks by the UI (#543). Static Hebrew text has no Latin letters, names included. Do not put a colon or bracket directly after a Latin word typed in a Hebrew sentence without checking the display. Preview with `?lang=he` (HE-09).
10. No left or right, above or below (HE-11).
11. Do not write a verb or pronoun after a placeholder in a form that only fits one gender, when the placeholder can be a body or a person of either gender (HE-15).
12. Every Hebrew string is "proposed, needs native review" until signed off (HE-14).

## Rules

### HE-01 Parity with English
Status: observed. Reason: a missing key throws an error and a mismatched placeholder shows the wrong value. Today the two files have 218 keys each and no mismatch in key names or placeholder indexes (checked by script). The repo tests this: `test_hebrew_keys_match_english_and_every_value_is_nonempty` and `test_hebrew_keeps_complete_format_tokens_and_logical_text_order`, and the Unity test `InHebrewEveryStaticTextIsTheHebrewString`.
Check: the repo's tests; a pattern search over the strings files as a local convenience.

### HE-02 One Hebrew word per concept
Status: proposed, native. Reason: the same concept can have more than one Hebrew word, and in places one Hebrew word covers two English concepts (see the glossary). Apple's guidance asks for a common-terms list used consistently.

Settled by the owner in #550 (shown so nobody reopens them by mistake):
- Seats and members: a unit string by body, "מנדטים" for an elected body (`cabinet.seats`) and "חברים" for the appointed Provisional State Council (`cabinet.seats_appointed`). A repo test pins both. The older `cabinet.members_unit` ("חברים") is still in the file.
- Minister rating: "כישורים" (`card.competence`), beside "נאמנות" (`card.loyalty`). It was "כשירות" on 14 October.
- Ladder caption: "המצב הביטחוני" (`defence.section_ladder`). It was "דרגת ביטחון" on 14 October.
- Words for the resource layer, decided by the owner on 15 October: כסף, מזון, נשק and תמיכה בינלאומית, with לכידות חברתית for Social cohesion (`docs/gdd/cutover-resource-layer.md`). The top-bar captions still say אוצר and מעמד בינלאומי until the loop lands.
- Office, government and body names: sourced Hebrew forms are in the content since #558, from the Knesset's records where they give one (the `title_he`, `name_he` and `body_he` fields), and the English titles stay the player's default.

Still open:
- The ladder's own words. "דרגה {0} מתוך 5" (`hud.level`) and "הורדת הדרגה" (`defence.lower`) use one word, and "רמת ביטחון {1} מתוך 5" (`unit.national`) uses another. The five rung lines (`defence.rung1` to `defence.rung5`) number the steps, and the Hebrew README says "סולם הסלמה". English says "Level" and "security level".
- Settlement and locality: "יישובים: {0}" (`info.owned`) and "יישובים ב-1948: {0}" (`info.localities`) use one word for two English concepts.
- Cabinet and government: "ממשלה" labels the Cabinet screen (`hud.nav.cabinet`) and is also the word for a government, where the English separates them. The content's government names (ממשלת ישראל הראשונה and so on) repeat the word.
- Terrain: "בקע" (`info.biome.valley`) for "Valley" and "עמק" (`info.biome.lowland`) for "Inland lowland". They may be swapped. "עמק" appears to be the usual word for a valley and "בקע" a rift or basin, which the reviewer should confirm.
For the native reviewer: choose the word for each open concept above and record it in the glossary's Hebrew column.

### HE-03 Form of address
Status: proposed, native; source read directly. Source: the Israeli National Digital Agency's guide to government language, section 1.3.3 (paraphrased; reuse terms not found). It says: do not address users only in the masculine singular; do not use slash or dot forms; first priority is a setting that adapts the form to the user; second, a second person without a gender marker (words ending in ך, ת or ה); then a neutral first person; then an action noun, an infinitive, or rephrasing such as "יש לשלוח".
- The strings already follow this apart from one masculine imperative: "הסתר" (`event.hide`). Candidate: "הסתרה" or "להסתיר".
- Five strings use "יש ל...": for example "יש ללחוץ על המפה כדי לבדוק משושה" (`info.hint`). Since #550 there are ten action-noun labels, among them "הקמת מעברה ({0})" (`info.build_camp`), "הגשת התקציב" (`budget.submit`), "העלאת הדרגה" (`defence.raise`), "השמעת ההקלטה" (`start.listen`) and "איפוס" (`budget.reset`). One uses the ך ending: "{0} (מינוי שלך)" (`card.appointed_name`).
- Two forms the reviewer should look at: "טוען את ההקלטה…" (`start.loading`), a masculine present-tense form with the program as its implied subject; and "המשך" (`start.continue`), which reads as a noun and also matches a masculine imperative. The Hebrew README addresses the reader as "אתם" (plural), a different choice again.
- A player setting for the form of address is the guide's first priority. It is a design decision for the owner and is not proposed here.
For the native reviewer: confirm that "יש ל..." and action nouns are right for a game, rule on the two forms above, and choose between "הסתרה" and "להסתיר".

### HE-04 Counts and plurals
Status: observed in the Hebrew strings, maintainer for a mechanism. Reason: Hebrew has three plural categories for cardinal numbers (one, two, other; Unicode CLDR 48), and the game has no general way to choose a form by count. The Hebrew file already writes counts as "Label: N": "החלטות ממתינות נוספות: {0}" (`event.more`), which needs no plural form, and a repo test pins it as count-neutral. One place picks between two keys by count: "{0:0} נקודה" (`hud.say_point`) and "{0:0} נקודות" (`hud.say_points`). Two keys cover one and other, and not the separate category for exactly 2.
- Gendered numerals (the form of a number depends on the gender of the counted noun) are a separate question. No source was found, and the rule is not written here.
For the native reviewer: list any strings where a number appears next to a noun and say which form is needed, and say whether the two-key form of `hud.say_point` is enough for a digit numeral.

### HE-05 Spelling
Status: proposed, native. Reason: the Academy of the Hebrew Language calls full spelling (ktiv male) the main spelling of Hebrew today, and r12a's notes say it is the predominant approach in everyday use. Proper names often keep traditional spelling (the Academy's examples: יעקב, משה, ירושלים).
For the native reviewer: confirm full spelling for all UI text, and decide the spelling of historical names that content will need.

### HE-06 Punctuation
Status: proposed, native.
- Hebrew uses ASCII punctuation: full stop, comma, question mark, exclamation mark and colon work as in English, and the question mark is not mirrored (r12a).
- Acronyms take gershayim before the last letter, for example "הרמטכ״ל" and "האו״ם". The correct character is the typographic gershayim ״ (U+05F4); a straight quote is a common substitute because of keyboards, and r12a notes it sits too high (r12a). The Academy's own examples use the straight quote and do not discuss the typographic character. All four strings that have gershayim already use ״ (`defence.command`, `defence.ceasefire`, `defence.ceasefire_stops`, `defence.ceasefire_starts`), so the file is consistent. The abbreviation mark geresh is the typographic ׳ (U+05F3), in "מס׳ 1" (`start.source`) and in `info.hex`. Recommendation: keep ״ and ׳, record them as the rule, and fix any exception.
- Quotation marks are not paired. In principle ” opens and closes and ’ nests, but straight quotes are common in practice (r12a). The strings contain no double quotation marks. One places straight single quotes around a placeholder: "{0} לא מוכר: '{1}'" (`order.unknown`), where the quoted value is a raw id (UI-07). Choose one style before content needs it.
- The content now has a straight quote where the strings have the typographic character: the Haganah post is given as רמטכ"ל ההגנה in `content/offices.yaml`, four party names are given as מפא"י, מפ"ם, מק"י and הצה"ר in `content/parties.yaml`, and the Defence screen says הרמטכ״ל. One character should be chosen for strings and content alike.
For the native reviewer: confirm ״ and choose a quotation style.

### HE-07 Maqaf
Status: proposed, native. Reason: the Academy's punctuation rules use a maqaf when a prefix meets a numeral or Latin letters, for example "ה־12" and "ב־DNA". r12a says the maqaf is the proper character for a hyphen between compounds, that keyboards often lack it so a hyphen-minus is substituted, and that lines should not break next to it.
- Today: "יישובים ב-1948: {0}" (`info.localities`) uses a hyphen-minus. "מ־{0} עד {1}" (`why.turn`) uses a maqaf. The date pattern joins the prefix to the month name with no hyphen ("{0} ב{1} {2}", `date.day_month_year`), which is ordinary Hebrew for a prefix before a word.
- Candidate: "יישובים ב־1948: {0}".
- A second place: the map legend joins two colour words with a hyphen-minus, "כתום-אדום" (`map.legend_held`, also `map.legend_armistice`). r12a's note on the hyphen between compounds points to the maqaf there too. Candidate: "כתום־אדום".
For the native reviewer: confirm the maqaf for prefixes before numerals and Latin letters, for the colour compound, and the numeral range style in `why.turn`.

### HE-08 Numbers, dates and money
Status: proposed, maintainer, code.
- Digits are Latin. A range written with a hyphen-minus reads left to right inside Hebrew text (r12a), while the Academy writes a numeric range right to left with an en dash, the first number at the right (פרקים 5–12, not 12–5). The two behave differently under the bidi algorithm, so avoid typed ranges, as the strings already do with "מ־{0} עד {1}" (`why.turn`), and test any range in Unity before adopting one.
- Dates and money are formatted by the simulation, in English, and are inserted into Hebrew strings. That produces lines like "אוצר IL 18.6m" with Latin currency codes in the middle of Hebrew. Since #550 the strings files hold Hebrew month names (`date.month_1` to `date.month_12`, from "ינואר" to "דצמבר") and two patterns, "{0} ב{1} {2}" (`date.day_month_year`) and "{0} {1}" (`date.month_year`). By `git grep` only the map's control captions use them. The formatter's dates (the top bar's date, the Why panel) are still English, and a repo test says so ("the date is still English (#55)"). Money is untouched. Since #543 the UI wraps each value it puts into a Hebrew pattern in invisible left-to-right marks, so these English values read as one run, though they are still English. Routing the formatter through the same keys needs a change to `PlayerText`, which is Eyal's code.
- Currency needs a decision. The money format is "IL 1.2m". For the years the game covers, "IL" is, as far as is known, the Israeli pound (an inference, not checked in a source), not the new shekel, so the shekel sign ₪ that Hebrew UI guidance normally uses would be wrong. How the Israeli pound is written in Hebrew is a question for the native reviewer and Eyal.
For the native reviewer: confirm the twelve month names as the style the game should use, supply the Hebrew way to write the Israeli pound, and the format for large amounts ("1.2m"). The spoken form already says "מיליון" (`hud.say_million`).

### HE-09 Mixed direction
Status: proposed, native, test in Unity. Reason: Hebrew runs right to left and embedded Latin text and numbers run left to right. The base direction must be set, or runs are misordered (r12a); W3C and Unicode advise isolating each opposite-direction run and any value of unknown direction (W3C; r12a recommends the isolate characters over embeddings). Unity's advanced text generator supports Hebrew and a direction setting, but its manual does not mention isolates, so they must be tested in the game.
- To test: "לא ניתן היה להפעיל את Statecraft: {0}. יש לטעון את הדף מחדש." (`boot.failed`), where a colon follows a Latin word and a placeholder follows it.
- To test: "לחיצה, Enter או רווח לדילוג · Esc מדלג על הכול" (`outcome.skip`), which is new since 14 October.
- Settled since 14 October: the recording credit keeps no Latin name. It is "הקלטה: ראלף הלינגר, ארכיון המדינה" (`start.recording_credit`), as the Israel State Archives spell the name, and the Hebrew UI test rejects Latin letters in any static Hebrew text, names included.
- Already in place: each text takes its direction from its own first letter (`InHebrewEachTextTakesItsDirectionFromItsOwnWords`), and the Hebrew test bans the explicit embedding and override characters U+202A to U+202E. Since #543 every value inserted into a Hebrew pattern is wrapped in left-to-right marks (U+200E), and `HebrewValuesTests` renders the lines to check that a minus sign and an English date draw correctly and that the marks draw nothing. That settles inserted values. A Latin word typed inside a Hebrew sentence is not covered by the tests reviewed.
- How to see it: open the game with `?lang=he`.
- To test: "ספיטפייר LF Mk IXe" (`unit.aircraft.spitfire`).
- To test: in the game, the lines that receive an English date or amount, to confirm the marks do what the rendered test describes (HE-08).
For the native reviewer: say how each of these should read.
For the maintainer: the #543 check found that the Hebrew face honours U+200E and draws nothing for it. Whether it honours the isolate characters is not tested.

### HE-10 Latin names and terms inside Hebrew
Status: proposed, native. The product name appears in Latin inside a Hebrew sentence ("Statecraft" in `boot.failed`, which is not a static text), and aircraft and place names mix scripts. Since #558 the recording credit uses a transliterated name. Decide per category whether a name is transliterated or kept in Latin, and record it in the glossary.
For the native reviewer: decide for the product name, aircraft names (the strings already transliterate "Avia" as "אוויה"), and the names of places and people. The credit line is settled: "הקלטה: ראלף הלינגר, ארכיון המדינה" (`start.recording_credit`).

### HE-11 Layout and directional words
Status: observed in English, proposed for Hebrew. The English file has no "left", "right", "above" or "below" (checked). Google advises against directional words because they fail accessibility and localisation, and in the mirrored layout "the button on the right" would be wrong. r12a lists punctuation that should not start or end a line (closing quotes and brackets, . , ; ! ? ־ %) and says a currency sign stays with its number; this is a layout property for engineering to check.
Check: a pattern search over the strings files.

### HE-12 Content text (events, units, names)
Status: maintainer (#55). Event text and unit labels arrive in English today. Names of offices, parties, governments, legislatures and places have sourced Hebrew forms in the content since #558, but only the places' names are read by the UI so far. If content is localised, the same rules apply: every historical claim keeps its sources, no quote is invented, and Hebrew names of people and places are checked against a source and not guessed. Sensitive events need review by a native reader and the existing sensitivity review, in addition to the historian review.
For the maintainer: whether and when content gets Hebrew, and who reviews it.

### HE-13 Tone
Status: proposed, native. The project voice is sober, direct and institutional. Hebrew should match: no slang, no drama, no filler. The government guide's principle of personal but gender-neutral wording (HE-03) applies. No Hebrew-specific tone source has been found beyond that.
For the native reviewer: say what register suits a sober political strategy game, and name two or three sentences that sound right.

### HE-14 Review and sign-off
Status: proposed. Every Hebrew string and every rule in this guide stays "proposed, needs native review" until a native reviewer has signed it. Keep a review log with the date, the reviewer's name, the keys or rules reviewed, and the changes made. A reviewer's change is recorded as a decision with its reason, so later edits do not undo it.

### HE-15 Agreement with a placeholder
Status: proposed, native, code. Reason: a Hebrew verb, adjective or pronoun agrees in gender and number with its subject, and a placeholder can be filled with a name of either gender. Several sentences fix the form after `{0}` as masculine: "{0} מצביע עליו, אך הצבעתו אינה מחייבת: לקואליציה יש {1} מתוך {2} {3}" (`budget.vote_advisory`), "{0} אינו מצביע על התקציב" (`budget.no_vote`) and "מתייעצת עם {0} · {1} חברים · הצבעותיו אינן מחייבות" (`cabinet.legislature_advisory`). The two bodies those sentences name appear to be feminine nouns in Hebrew ("הכנסת", "המועצה"). The problem is hidden today because the body's name arrives in English. Since #558 the content holds the Hebrew body names, and the owner already handles gender in data for office titles, with a separate feminine title field where a woman held the office. The UI does not read the body names yet, so the problem will show when it does. A body may need a gender field of its own, or the sentences a structure that does not need one.
For the native reviewer: say whether these sentences need a structure that does not depend on the gender of `{0}`, and mark any other string with a verb or pronoun after a placeholder.

## Candidate fixes for the Hebrew file (all unapproved)

| Key | Today | Candidate | Rule |
|---|---|---|---|
| `event.hide` | הסתר | הסתרה, or להסתיר | HE-03 |
| `info.localities` | יישובים ב-1948: {0} | יישובים ב־1948: {0} | HE-07 |
| `map.legend_held` | כתום-אדום (in the line) | כתום־אדום | HE-07 |
| `unit.national` | רמת ביטחון {1} מתוך 5 | the same word as `hud.level` (דרגה) | HE-02 |
| `info.biome.valley`, `info.biome.lowland` | בקע, עמק | reviewer to say whether the two are swapped | HE-02 |
| `start.loading` | טוען את ההקלטה… | reviewer to rule on the masculine present form | HE-03 |
| `budget.vote_advisory`, `budget.no_vote`, `cabinet.legislature_advisory` | masculine forms after `{0}` | a structure that does not depend on the gender of `{0}` | HE-15 |
| `boot.failed` | ...את Statecraft: {0}. ... | check the display; isolate the Latin name | HE-09 |

Settled by the owner since 14 October and removed from this table: `card.competence` (now כישורים), `defence.section_ladder` (now המצב הביטחוני) and the separate unit for the Provisional State Council (`cabinet.seats_appointed`).

## Review checklist

Run in order. A "no" is a finding, cited by rule ID.

1. Does the key exist in English with the same placeholders (HE-01)?
2. Does it use the glossary's Hebrew word for each concept (HE-02)?
3. No masculine imperative or slash form; action noun, "יש ל...", ך or ת endings, or a neutral first person (HE-03)?
4. Counts as "Label: N" (HE-04)?
5. Full spelling (HE-05)?
6. Gershayim as ״, one style across the file (HE-06)?
7. Maqaf before a numeral or Latin letters (HE-07)?
8. No typed date or money; flag any string that receives English-formatted values (HE-08)?
9. Latin text and unknown-direction values isolated, and the display checked (HE-09, HE-10)?
10. No directional words (HE-11)?
11. No verb or pronoun after a placeholder in a form that fits only one gender (HE-15)?
12. A native reviewer named and dated (HE-14)?

## Open decisions

For the maintainer:
- Localise the formatter's dates (the `date.*` keys already exist) and money, and decide how the Israeli pound is written in Hebrew (HE-08).
- Whether isolates are honoured by the text generator, and where the test lives (HE-09). Per-text direction is already tested.
- Hebrew for content, and its review (HE-12, #55).
- A player setting for the form of address (HE-03).
- Whether the two-key plural is enough, or a general mechanism is wanted (HE-04).
- Gender agreement once the Hebrew content names are read by the UI (HE-15).
- One character for gershayim across strings and content (HE-06).

For the native Hebrew reviewer: every "native" item above, the candidate fixes, and the register (HE-13).

## Evidence and limits

- Read directly by the author: the Israeli National Digital Agency guide to government language (section 1.3.3, slides 52 to 57); r12a "Modern Israeli Hebrew" orthography notes (updated 27 April 2026, CC BY 4.0); the W3C "Hebrew Script Resources" index (Group Note Draft, 20 March 2026); the real strings and code named above.
- Re-opened and checked by the author on 14 October 2026: the Academy of the Hebrew Language punctuation and spelling pages, the W3C inline bidi article, the Unity manual page, Unicode CLDR 48 plural rules, and the Google and Apple pages used here.
- Not found: a Hebrew-specific source on UI tone and register, gendered numeral agreement in UI, and an authoritative Knesset source for the Council and Knesset terms. The Microsoft Hebrew guide was excluded by choice.
- The 15 October update added no new external source. Its new facts come from the strings snapshot and from read-only `git grep` and `git show` on `upstream/main` 50ba5d5c: the test names, the per-text direction, the date keys and the plural pair. The Hebrew claims about gender agreement and about the words for valley and lowland are the author's reading and are marked as questions for the reviewer.
- The government guide is written for public digital services. It is a strong reference for Hebrew UI practice, not a rule for a game.

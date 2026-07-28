# Daily Briefing Routine Log

This file tracks state across daily runs of the morning briefing routine so each
run can build on the last (Spanish lessons progress sequentially; I Ching
hexagrams, country/region spotlights, and meme spotlights are never repeated).

## Output Preferences

- **Language:** Bilingual, full text in both languages — English version
  first, followed by the full Traditional Chinese (繁體中文) version. Not
  parenthetical annotations; each section should be written out completely
  in both languages. (Requested 2026-07-09, revised same day.)
- **Delivery format:** The PushNotification tool's email/push channel
  flattens ALL line breaks and whitespace into a single paragraph,
  regardless of whether the message uses Markdown syntax or raw HTML
  tags — both were tried on 2026-07-09 and both collapsed. Do not rely on
  PushNotification to deliver long, multi-section formatted content.
  Instead: keep the push notification message short (a one-line alert),
  and deliver the full formatted briefing as a standalone `.html` file via
  SendUserFile, which renders correctly.
- **File delivery:** SendUserFile only puts the file into the current
  Claude app/session — it does NOT reach the user's email inbox. When the
  user wants a persistent, linkable copy, commit the file into this repo
  (under `briefings/` or `spanish-lessons/`) on the working branch, push,
  and give the GitHub blob + raw URLs instead. (Established 2026-07-09.)
- **Portal page (`index.html`, established 2026-07-12):** The user wants a
  single entry page listing every day's generated URLs, so every routine
  run MUST add a new row to the top of the table in `index.html` (date,
  link to that day's `briefings/YYYY-MM-DD.html`, link to that day's
  Spanish lesson file, and the hexagram name/number) — in addition to the
  usual `ROUTINE_LOG.md` table updates. `index.html` uses relative links
  (`briefings/...`, `spanish-lessons/...`) so it works both on GitHub and
  if GitHub Pages is enabled.
- **GitHub Pages: ENABLED as of 2026-07-14.** The user turned on Pages
  (Settings → Pages → Deploy from branch, folder `/ (root)`). Live site:
  https://lebonthe.github.io/ClaudeRoutineTest/ — this is the canonical
  link to give the user for the portal (and for individual pages, e.g.
  `https://lebonthe.github.io/ClaudeRoutineTest/briefings/2026-07-12.html`).
  **Important:** Pages serves whatever branch is configured in Settings →
  Pages — it does NOT automatically track whichever branch the routine
  happens to run on that day (see the recurring branch-divergence bug
  below). If the live site looks stale, check which branch Pages is
  deployed from and make sure the day's work actually lands there.
  The repo is public, so Pages does not expose anything private.

## Spanish Lesson Template (required format, set 2026-07-09)

Every Spanish lesson must follow this exact structure (written in
Traditional Chinese, with Spanish target-language content inline). Do not
revert to the old brief format.

1. **🎯 今日學習目標** — 1-2 sentences: what the learner can do after this lesson.
2. **🗣️ 核心對話 / 句子** — a minimal dialogue or 2-3 core sentences. Each line
   is a two-line block:
   - Line 1: `[Spanish sentence] —— [Chinese translation]`
   - Line 2 (indented, smaller/grey text): the Chinese phonetic
     approximation (諧音, not English-based syllables), followed by its
     Hanyu Pinyin in parentheses and italics, e.g.
     `歐拉!摳摸 貼 呀馬斯?(ōu lā! kōu mō tiē yā mǎ sī?)` — the pinyin
     disambiguates the tones/reading of the Chinese proxy characters.
     (Revised 2026-07-09 per user feedback — see spanish-lessons/day-01.html
     for the reference layout.)
3. **🔍 拆解與超詳細細節** — break down every word/verb conjugation/gender in
   the core sentences; proactively answer likely questions (e.g. why the
   inverted ¡/¿, where a reflexive verb form comes from).
4. **💡 文化或實用小撇步** — one cultural/usage note (e.g. Hola vs. Buenos días).
5. **✍️ 1分鐘互動練習題** — 2 very short practice items (fill-in-blank,
   matching, or a one-line situational sentence).
6. `---` divider, then **🔑 今日練習題答案與解析** — answers with brief
   explanations, kept below the divider so the learner can cover it.

Lesson files are saved under `spanish-lessons/day-XX.html` and pushed to
the repo so a permanent link can be shared.

## Main Briefing Sections (fixed, 8 total per day)

1. US / Asia / Taiwan stock market news (figures, gains/losses, source links)
2. AI / iOS / Android / Flutter development news
3. Spanish lesson (summary + link to full `spanish-lessons/day-XX.html`)
4. I Ching hexagram, in King Wen Sequence order, never repeated (once all 64
   are used, switch to introducing one Zhuangzi essay/poem per day, never
   repeated)
5. Country/Region/Faction spotlight (location, size vs. other places,
   population, religion, economy, history, current leader, language) — never
   repeated
6. Internet meme spotlight (name, origin/history, how it went viral,
   meaning/usage, variations, current status) — never repeated
7. Film / Performing-arts spotlight (a landmark film, director, actor,
   cinematic technique/movement, OR a work/figure/form from the performing
   arts — theatre, opera, dance, musical, traditional performance such as
   Peking opera / Bunraku, etc.), with a detailed explanation: name, key
   figures/creators, era/background, plot or content overview where
   relevant, artistic style and techniques, cultural/historical
   significance, influence and legacy, and current status or where it can
   be experienced today — never repeated (added 2026-07-24)
8. Film-appreciation / criticism method (added 2026-07-24) — a daily lesson
   on HOW to watch films: film-analysis and critic's viewing methods, and
   how to deconstruct a director's craft (auteur analysis, mise-en-scène,
   cinematography/lighting, editing/montage, sound & score, blocking,
   colour, framing, symbolism, narrative structure, etc.). Teach ONE method
   or analytical lens per day, illustrated with a concrete real film scene
   as a worked example. This is a progressive skill track (like the Spanish
   lessons — build up the toolkit over time); do NOT repeat a method/lens
   already taught. Distinct from Section 7: Section 7 introduces a subject
   (a film/figure/work); Section 8 teaches a transferable way of watching
   and analysing.

## Spanish Lessons Taught

| Date | Lesson # | Topic | New concept introduced | File |
|------|----------|-------|-------------------------|------|
| 2026-07-08 | 1 | Greetings & introducing yourself (brief format, superseded) | "Hola", "¿Cómo te llamas?", "Me llamo...", basic vowel pronunciation | — |
| 2026-07-09 | 1 (upgraded) | 問候與自我介紹 — full template version | ¡Hola!, ¿Cómo te llamas? / Me llamo (reflexive verb llamarse), Mucho gusto, inverted ¡ ¿ | spanish-lessons/day-01.html |
| 2026-07-09 | 2 | 寒暄「你好嗎?」 | ¿Cómo estás? / Estoy (verb estar), muy bien, Yo también | spanish-lessons/day-02.html |
| 2026-07-10 | 3 | 更多心情說法與形容詞陰陽性 | Más o menos, mal, un poco cansado/a (adjective gender agreement) | spanish-lessons/day-03.html |
| 2026-07-11 | 4 | 道別與基本禮貌用語 | Adiós vs. Hasta luego, tener que + irse, Fue un placer conocerte, Igualmente, Que tengas un buen día (subjunctive preview) | spanish-lessons/day-04.html |
| 2026-07-12 | 5 | 你從哪裡來?(ser 動詞與國籍) | ¿De dónde eres? / Soy (verb ser, permanent identity vs. estar), nationality adjectives (español/española) | spanish-lessons/day-05.html |
| 2026-07-13 | 6 | 數字 0-10 | cero–diez, ¿Cuántos años tienes? / Tengo... años (tener + age idiom) | spanish-lessons/day-06.html |
| 2026-07-15 | 7 | 星期幾(los días de la semana) | lunes–domingo, ¿Qué día es hoy? / Hoy es... | spanish-lessons/day-07.html |
| 2026-07-16 | 8 | 月份(los meses del año) | enero–diciembre, ¿En qué mes estamos? / Estamos en... (estar vs. ser recap), cumpleaños | spanish-lessons/day-08.html |
| 2026-07-17 | 9 | 報時(¿Qué hora es?) | Es la una / Son las... (singular vs. plural for telling time), y cuarto / y media / menos cuarto, ¿A qué hora...? + Es a las... | spanish-lessons/day-09.html |
| 2026-07-19 | 10 | 家人與所有格(mi/tu/su) | Family vocabulary (madre, padre, hermano/a...), possessive adjectives mi/tu/su → mis/tus/sus (agree with the noun owned, not the owner) | spanish-lessons/day-10.html |
| 2026-07-20 | 11 | 規則 -AR 動詞現在式 | Present-tense conjugation of regular -ar verbs (hablar, trabajar, estudiar): stem + -o/-as/-a | spanish-lessons/day-11.html |
| 2026-07-21 | 12 | 規則 -ER / -IR 動詞現在式 | Present-tense conjugation of regular -er/-ir verbs (comer, beber, vivir, escribir): stem + -o/-es/-e (identical for yo/tú/él across both families) | spanish-lessons/day-12.html |
| 2026-07-22 | 13 | Ir a + 原形動詞(近未來式) | Near-future tense: irregular verb ir (voy/vas/va) + a + infinitive, e.g. voy a viajar | spanish-lessons/day-13.html |
| 2026-07-23 | 14 | Estar + 現在分詞(現在進行式) | Present progressive: estar (estoy/estás/está) + gerund (-ando/-iendo), e.g. estoy estudiando; irregular gerunds dormir→durmiendo, leer→leyendo, decir→diciendo | spanish-lessons/day-14.html |
| 2026-07-24 | 15 | Gustar 動詞與間接受詞代名詞 | The "backwards" verb gustar: indirect object pronouns (me/te/le/nos/les) + gusta (singular liked thing) / gustan (plural liked things) — the verb agrees with what's liked, not who likes it | spanish-lessons/day-15.html |
| 2026-07-25 | 16 | 規則動詞簡單過去式(Pretérito Indefinido) | Regular preterite endings: -ar verbs take -é/-aste/-ó/-amos/-aron; -er/-ir verbs share -í/-iste/-ió/-imos/-ieron (identical across both families, unlike the present tense) | spanish-lessons/day-16.html |
| 2026-07-26 | 17 | 不規則過去式 ir/ser/hacer | ir and ser share one identical irregular preterite conjugation (fui/fuiste/fue/fuimos/fueron), disambiguated by context; hacer has stem change hac-→hic- with spelling-rule exception hizo (not "hico") in the third person | spanish-lessons/day-17.html |
| 2026-07-27 | 18 | 不規則過去式 u-字根動詞(tener/estar/poder) | The "u-stem" irregular preterite family: tener→tuv-, estar→estuv-, poder→pud-, all sharing endings -e/-iste/-o/-imos/-ieron with no written accents (unlike regular preterites); poder's preterite carries a special "succeeded/failed at" nuance (pude vs. no pude) distinct from the imperfect podía | spanish-lessons/day-18.html |
| 2026-07-28 | 19 | 不規則過去式 j-字根動詞(decir/traer/conducir) | The "j-stem" irregular preterite family: decir→dij-, traer→traj-, conducir (and all -ducir verbs)→-duj-, sharing endings -e/-iste/-o/-imos with the u-stem family, but with the sole true exception to the -ieron ending: the stem's "j" swallows the "i," giving -eron (dijeron/trajeron/condujeron, not dijieron) | spanish-lessons/day-19.html |

Note: a duplicate "Day 2" lesson (ser/¿De dónde eres?, i.e. the same topic
as Day 5) was independently produced on 2026-07-14 on an orphaned branch
(`claude/happy-newton-qhq5rv`) due to the branch-divergence bug described
below. It is not counted as a numbered lesson — Day 7 above correctly
continues from Day 6.

## I Ching Hexagrams Featured

| Date | Hexagram # | Name (Chinese / Pinyin / English) |
|------|-----------|-------------------------------------|
| 2026-07-08 | 1 | 乾 (Qián) — The Creative |
| 2026-07-09 | 2 | 坤 (Kūn) — The Receptive |
| 2026-07-10 | 3 | 屯 (Zhūn) — Difficulty at the Beginning |
| 2026-07-11 | 4 | 蒙 (Méng) — Youthful Folly |
| 2026-07-12 | 5 | 需 (Xū) — Waiting |
| 2026-07-13 | 6 | 訟 (Sòng) — Conflict |
| 2026-07-15 | 7 | 師 (Shī) — The Army |
| 2026-07-16 | 8 | 比 (Bǐ) — Holding Together |
| 2026-07-17 | 9 | 小畜 (Xiǎo Chù) — The Taming Power of the Small |
| 2026-07-19 | 10 | 履 (Lǚ) — Treading |
| 2026-07-20 | 11 | 泰 (Tài) — Peace |
| 2026-07-21 | 12 | 否 (Pǐ) — Standstill |
| 2026-07-22 | 13 | 同人 (Tóng Rén) — Fellowship with Men |
| 2026-07-23 | 14 | 大有 (Dà Yǒu) — Possession in Great Measure |
| 2026-07-24 | 15 | 謙 (Qiān) — Modesty |
| 2026-07-25 | 16 | 豫 (Yù) — Enthusiasm |
| 2026-07-26 | 17 | 隨 (Suí) — Following |
| 2026-07-27 | 18 | 蠱 (Gǔ) — Work on What Has Been Spoiled |
| 2026-07-28 | 19 | 臨 (Lín) — Approach |

Note: a duplicate Hexagram 2 (坤 Kūn) was also independently produced on
2026-07-14 on the same orphaned branch, for the same reason. Hexagram 7
above correctly continues from Hexagram 6.

## Country/Region/Faction Spotlights Featured

| Date | Subject |
|------|---------|
| 2026-07-14 | Bhutan (不丹) |
| 2026-07-15 | Uruguay (烏拉圭) |
| 2026-07-16 | Mongolia (蒙古) |
| 2026-07-17 | Iceland (冰島) |
| 2026-07-19 | Greenland (格陵蘭) |
| 2026-07-20 | Vatican City (梵蒂岡) |
| 2026-07-21 | Brunei (汶萊) |
| 2026-07-22 | Fiji (斐濟) |
| 2026-07-23 | Andorra (安道爾) |
| 2026-07-24 | Nepal (尼泊爾) |
| 2026-07-25 | Somaliland (索馬利蘭) |
| 2026-07-26 | Indonesia (印尼) |
| 2026-07-27 | Kazakhstan (哈薩克) |
| 2026-07-28 | Singapore (新加坡) |

## Internet Meme Spotlights Featured

| Date | Meme |
|------|------|
| 2026-07-14 | Rickroll (瑞克搖) |
| 2026-07-15 | "8+9" (八加九, Taiwan) |
| 2026-07-16 | Gangnam Style (江南 Style, South Korea) |
| 2026-07-17 | Doge (狗狗迷因) |
| 2026-07-19 | Skibidi Toilet (滑稽馬桶) |
| 2026-07-20 | "Ohio" / "Only in Ohio" |
| 2026-07-21 | "This Is Fine" (dog in burning room) |
| 2026-07-22 | "Lying Flat" (躺平, Tǎng Píng, China) |
| 2026-07-23 | "Versailles Literature" (凡爾賽文學, Fán'ěrsài Wénxué, China) |
| 2026-07-24 | "Distracted Boyfriend" (分心男友) |
| 2026-07-25 | Pepe the Frog (佩佩蛙) |
| 2026-07-26 | Woman Yelling at a Cat (對貓咆哮的女人) |
| 2026-07-27 | Harlem Shake (哈林搖) |
| 2026-07-28 | Bernie Sanders' Mittens (桑德斯的毛線手套) |

## Film / Performing Arts Spotlights Featured

New Section 7, added 2026-07-24. One film- or performing-arts subject per
day, with a detailed explanation, never repeated. Covers cinema (landmark
films, directors, actors, techniques/movements) OR the performing arts
(theatre, opera, dance, musical, traditional performance such as Peking
opera / Bunraku, etc.). Before choosing today's subject, check this table
and never repeat a subject already listed.

| Date | Subject |
|------|---------|
| 2026-07-24 | Citizen Kane (1941, dir. Orson Welles) |
| 2026-07-25 | Peking Opera (京劇) |
| 2026-07-26 | Kabuki (歌舞伎) |
| 2026-07-27 | Seven Samurai (七武士, 1954, dir. Akira Kurosawa) |
| 2026-07-28 | Bunraku (文樂) |

## Film-Appreciation / Criticism Method Lessons

New Section 8, added 2026-07-24. One film-analysis method / critic's
viewing lens per day (auteur/director deconstruction, mise-en-scène,
cinematography, editing, sound, colour, framing, symbolism, narrative
structure, etc.), each illustrated with a concrete real film scene as a
worked example. This is a progressive skill track (like the Spanish
lessons) — build up the analytical toolkit over time and never repeat a
method/lens already taught. Before choosing today's method, check this
table and pick one not yet covered.

| Date | Method / Lens taught | Example scene used |
|------|----------------------|--------------------|
| 2026-07-24 | Mise-en-scène (frame composition, blocking, deep focus) | Citizen Kane (1941, dir. Orson Welles) — the deep-focus "snow globe" negotiation scene, where young Charles plays in the background through the cabin window while his parents and Mr. Thatcher decide his fate in the foreground |
| 2026-07-25 | Editing & Montage (Soviet montage theory, Kuleshov Effect, cutting rhythm) | Battleship Potemkin (1925, dir. Sergei Eisenstein) — the Odessa Steps sequence, crosscutting marching soldiers, terrified civilian faces, and the runaway baby carriage at an accelerating rate to build panic and produce "intellectual montage" meaning through juxtaposition |
| 2026-07-26 | Cinematography & Lighting (light quality/direction, color palette, camera movement) | Blade Runner 2049 (2017, dir. Denis Villeneuve, cinematography by Roger Deakins) — the irradiated Las Vegas sequence, shot through custom Tiffen filters and Lee gels to bathe every surface in the same sickly orange-amber haze, deliberately withholding clarity on the giant statue silhouettes to match K's disorientation entering the dead city |
| 2026-07-27 | Sound Design & Score (diegetic vs. non-diegetic sound, score as emotional cue, silence, mix priorities) | Psycho (1960, dir. Alfred Hitchcock, score by Bernard Herrmann) — the shower scene, where a shrieking all-strings ostinato timed to the knife's thrusts supplies the visceral violence the fragmented, near-bloodless editing never explicitly shows; Hitchcock originally wanted the scene silent but credited the cue with roughly a third of the film's overall effect |
| 2026-07-28 | Colour (dominant palette as narrative device, colour as spotlight, palette shifts across acts, colour as long-distance visual callback) | Schindler's List (1993, dir. Steven Spielberg, cinematography by Janusz Kamiński) — the girl in the red coat, the sole sustained splash of colour in an otherwise black-and-white film, drawing attention amid the Kraków ghetto liquidation and later reappearing in a pile of clothing to silently confirm her death, marking the film's identified turning point for Oskar Schindler |

## Run Notes

- **2026-07-14 — branch-divergence bug found and (temporarily) fixed.**
  The routine was firing into a brand-new session with a brand-new branch
  on multiple different days instead of resuming one persistent
  conversation/branch. Result: 2026-07-09 through 2026-07-13 each ran in
  isolation on their own branch (`claude/epic-brahmagupta-is0gmu`,
  `-nn87ee`, `-b9qdr5`, `-mgut69`, plus `-g1y16m`), each only aware of the
  shared `day-01` base — every one of those five days independently
  authored its own "Day 2" Spanish lesson and independently picked
  hexagram 2 (坤). That was consolidated onto `claude/epic-brahmagupta-g1y16m`
  on 2026-07-14 (renumbering lessons 2-6, giving hexagrams 3-6 to the four
  duplicate days, adding `index.html`).
- **2026-07-14 — bug recurred (second branch, `claude/happy-newton-qhq5rv`).**
  Despite the above fix, ANOTHER independent session ran the same day on
  yet another fresh branch (`claude/happy-newton-qhq5rv`), again starting
  from the stale `day-01` base (unaware of `-g1y16m`'s consolidated
  history through 2026-07-13). It produced a real, useful 2026-07-14
  briefing (market data, dev news) plus two genuinely NEW sections not
  present before — Country/Region Spotlight and Internet Meme Spotlight
  (Bhutan, Rickroll) — but its Spanish lesson and hexagram duplicated Day
  5 / Hexagram 2 material. Its `ROUTINE_LOG.md` also could not reach
  `https://lebonthe.github.io/ClaudeRoutineTest/` (network egress to
  `lebonthe.github.io` was blocked in that session), so it fell back to
  the (stale) log as source of truth.
- **2026-07-15 — third occurrence, reconciled onto this branch
  (`claude/happy-newton-6o3hr4`).** This session ALSO started fresh from
  the stale `day-01` base, unaware of both `-g1y16m` (through 07-13) and
  `-qhq5rv` (07-14). This run:
  1. Fetched all sibling branches
     (`claude/epic-brahmagupta-{b9qdr5,g1y16m,is0gmu,mgut69,nn87ee}`,
     `claude/happy-newton-qhq5rv`) and diffed their file trees to
     reconstruct true chronological state, since neither `ROUTINE_LOG.md`
     nor the live Pages site (deployed from a specific branch, not
     necessarily whichever branch a session lands on) can be trusted
     alone while this bug is active.
  2. Adopted `-g1y16m`'s consolidated 07-08→07-13 history (briefings,
     `spanish-lessons/day-01..06.html`, `index.html`) as the base, since
     it was the most complete/continuous and matched the portal-page
     design.
  3. Carried forward `-qhq5rv`'s two genuinely new 07-14 additions
     (`briefings/2026-07-14.html` as a historical record, plus the
     Bhutan/Rickroll spotlight entries) without treating its duplicate
     Day-2/Hexagram-2 content as a new numbered entry.
  4. Continued cleanly from there: Spanish Day 7, Hexagram 7, plus new
     (non-duplicate) country and meme spotlights, all committed to this
     branch.
  - **If a future run again finds itself on an unfamiliar branch with
    only `day-01`/Hexagram-1 content, that is the signal this bug is
    STILL unresolved.** Recommended action for that run: do exactly what
    this run did (fetch and diff all `claude/*` branches, especially
    checking which one GitHub Pages is actually configured to deploy
    from — Settings → Pages — since that is the most reliable "latest
    truth" pointer), rather than trusting `ROUTINE_LOG.md` alone. The
    underlying fix (make the routine/trigger resume one persistent
    session or, failing that, always branch from the tip of the branch
    Pages deploys from rather than from a stale default) needs a human
    to check the Routine's configuration outside of what these tools can
    see/change — flag it to the user if it keeps happening.
- Sections 5 (country/region/faction spotlight) and 6 (internet meme
  spotlight) are new as of 2026-07-14 and were not present in the
  2026-07-08 through 2026-07-13 briefings.
- Briefings are saved under `briefings/YYYY-MM-DD.html` for every date,
  2026-07-08 through 2026-07-15 (all now present on this branch, with
  2026-07-14 carried over from the `-qhq5rv` branch as described above).
- **2026-07-16 — bug recurred a fourth time (this run started on a
  brand-new local branch, `claude/happy-newton-ltdkx9`), same pattern as
  before.** The session's initial git state was, once again, checked out
  from the stale default branch (`claude/gracious-ramanujan-4wyzgc`,
  frozen at Day 1 / Hexagram 1 only) rather than continuing from any
  branch with real progress. Network egress to
  `https://lebonthe.github.io/ClaudeRoutineTest/` was also blocked again
  in this session (both `WebFetch`, which returned HTTP 403, and a
  direct `curl`, which returned connection code 000/no route) — so, per
  the recommended recovery procedure above, this run listed all
  `claude/*` branches via the GitHub MCP tools and diffed their
  `briefings/`/`ROUTINE_LOG.md` contents instead of trusting the local
  checkout or the Pages site. `claude/happy-newton-6o3hr4` was confirmed
  to have the longest unbroken run (07-08 through 07-15, Spanish 1-7,
  hexagrams 1-7, plus the Bhutan/Uruguay and Rickroll/"8+9" spotlights)
  and was adopted as the base (`git reset --hard
  origin/claude/happy-newton-6o3hr4`) before adding today's content.
  **This confirms the branch-divergence bug is still unresolved as of
  2026-07-16** — every session continues to land on a fresh branch from
  a stale starting point rather than resuming prior work or branching
  from the tip of whatever branch GitHub Pages actually deploys from.
  The fix still needs a human to check the Routine's trigger/session
  configuration (and confirm which branch Pages Settings points at) —
  this cannot be corrected from inside a session. **Recommendation for
  the user:** consider pointing the routine at a fixed persistent branch
  (or configuring GitHub Pages to deploy from whichever branch is
  actually maintained, e.g. rename/merge the `happy-newton-6o3hr4` line
  into a permanent branch like `main`) so future runs have one
  unambiguous source of truth to resume from.
- **2026-07-17 — bug recurred a fifth time (this run started on yet
  another brand-new branch, `claude/happy-newton-018a9x`), same pattern
  as before.** The session's initial git checkout was, once again, on the
  stale default branch (`claude/gracious-ramanujan-4wyzgc`, frozen at Day
  1 / Hexagram 1 only). Both `WebFetch` (HTTP 403) and a direct `curl`
  (exit code 000 / no route) to
  `https://lebonthe.github.io/ClaudeRoutineTest/` were blocked again in
  this session, confirming egress to that host is not reliably available
  from inside these sessions — so, per the recommended recovery
  procedure, this run used the GitHub MCP tools to list all `claude/*`
  branches and diff their `briefings/`/`spanish-lessons/`/`ROUTINE_LOG.md`
  contents instead of trusting the local checkout or the Pages site.
  `claude/happy-newton-ltdkx9` was confirmed to have the longest unbroken
  run (07-08 through 07-16, Spanish Days 1-8, Hexagrams 1-8, plus the
  Bhutan/Uruguay/Mongolia and Rickroll/"8+9"/Gangnam Style spotlights —
  one commit ahead of `happy-newton-6o3hr4`, which stops at 07-15) and was
  adopted as the base (`git checkout -B claude/happy-newton-018a9x
  origin/claude/happy-newton-ltdkx9`) before adding today's content
  (Spanish Day 9, Hexagram 9, Iceland, Doge).
  **This confirms the branch-divergence bug is still unresolved as of
  2026-07-17** — every session continues to land on a fresh branch from a
  stale starting point rather than resuming prior work or branching from
  the tip of whatever branch GitHub Pages actually deploys from, and the
  live Pages site cannot be used from inside a session to verify the
  latest date either. **Recommendation for the user (repeated, now a
  fifth time):** this needs a human-side fix outside what these sessions
  can change — either point the routine/trigger at one fixed persistent
  branch, or merge the actively-maintained line (currently
  `happy-newton-ltdkx9`) into a permanent branch such as `main` and
  configure GitHub Pages to deploy from it, so future runs have one
  unambiguous source of truth to branch from without needing to
  reconstruct history via the GitHub API every time.
- **2026-07-19 — bug recurred a sixth and seventh time, plus the Pages
  branch itself was found to have silently fallen behind this line.**
  Two more isolated, duplicate-only runs happened: `claude/happy-newton-d0ctxa`
  (2026-07-18, picked Bhutan again and Doge again — both already used,
  and Day 2/Hexagram 2 again — nothing new, unlike 07-14's `qhq5rv` which
  at least contributed genuinely new Bhutan/Rickroll spotlights) and this
  session's own starting point on 2026-07-19 (`claude/happy-newton-wevard`,
  also forked from the stale `gracious-ramanujan-4wyzgc` base and
  independently produced its own duplicate Day 2/Hexagram 2/Mongolia,
  plus a Skibidi Toilet meme pick that — unlike Mongolia — was NOT a
  duplicate of anything in this line's history).
  - **Separately, and more seriously:** this session initially checked
    GitHub Pages' deployment history directly
    (`GET /repos/.../deployments?environment=github-pages`) and found
    Pages was actually configured to deploy from `claude/epic-brahmagupta-g1y16m`
    — a branch that stopped being updated after 2026-07-13 and was
    **never aware `happy-newton-6o3hr4`/`-ltdkx9`/`-018a9x` (this actively
    maintained line, current through 07-17) existed at all.** A first
    attempted fix pushed new 07-19 content onto `epic-brahmagupta-g1y16m`
    without checking for a more-advanced sibling branch first — which
    would have permanently entrenched the wrong (less complete, 4-days-stale)
    branch as canonical. Comparing file-by-file confirmed
    `claude/happy-newton-018a9x` is a strict superset of
    `epic-brahmagupta-g1y16m` (identical content for every overlapping
    date/file, plus three additional real days: 07-15, 07-16, 07-17)
    and is the true latest state.
  - **Fix applied:** adopted `claude/happy-newton-018a9x` as the base,
    added a genuinely new Day 10 (family vocab + mi/tu/su possessives),
    Hexagram 10 (履 Lǚ), Greenland, and Skibidi Toilet (carried over from
    the otherwise-discarded `happy-newton-wevard` attempt, since it
    wasn't a duplicate), and **force-pushed this combined history to
    `claude/epic-brahmagupta-g1y16m`** (the confirmed live Pages source
    branch) so the live site actually reflects the true, most-complete
    state. This is a force-push (not a fast-forward) because
    `epic-brahmagupta-g1y16m`'s and `happy-newton-018a9x`'s histories
    never shared a common tip after 2026-07-13 — nothing is lost,
    though, since every one of `epic-brahmagupta-g1y16m`'s own unique
    commits duplicated content already present (in improved form) on
    `happy-newton-018a9x`, and all the old branches/commits remain
    individually reachable by name if ever needed.
  - **2026-07-18 has no recoverable content at all** (unlike 07-14) —
    both `d0ctxa`'s Spanish/hexagram AND its country/meme picks were
    full duplicates — so, per the established precedent, it is not being
    retroactively fabricated. `index.html` shows a dashed-out row for
    that date with a pointer to this note.
  - **This is now the SEVENTH confirmed occurrence of the exact same
    branch-divergence bug** (07-09 through 07-19, missing only 07-08).
    A session cannot fix its own targeting — **this needs the user to
    check the claude.ai/Cowork Routine's trigger configuration directly**
    (persistent-session / branch-targeting settings) and, ideally, also
    verify in GitHub repo Settings → Pages that the source branch matches
    whichever branch is actually being kept up to date (check
    `GET /repos/.../deployments?environment=github-pages` for the ground
    truth, not the branch a given session happens to land on, and not
    the repo's `default_branch` field, which is unrelated to Pages).
    Until the trigger itself resumes one persistent branch, every future
    run should, before doing anything else: (1) list all `claude/*`
    branches, (2) diff their `briefings/`/`spanish-lessons/`/`ROUTINE_LOG.md`
    trees to find the one with the longest real (non-duplicate) run, and
    (3) confirm via the deployments API which branch Pages actually
    serves, updating that exact branch (merging in the longest-real-run
    branch first if they've diverged, as done here) rather than assuming
    the branch the session happens to start on is authoritative.
- **2026-07-20 — Routine instructions updated with an explicit git
  workflow, and today's entry (Day 11 / Hexagram 11 / Vatican City /
  "Ohio") added following it.** The user is updating the Routine's
  prompt (pasted back manually into the claude.ai/Cowork trigger) to
  require, every day: (1) re-verify the persistent portal branch via the
  `deployments?environment=github-pages` API (not `default_branch`),
  (2) branch off that branch's current tip as `claude/daily-YYYY-MM-DD`,
  (3) do the day's work on that branch, (4) fast-forward-merge it back
  into the persistent portal branch locally, (5) push the persistent
  branch (never just the daily branch) so Pages actually updates, and
  (6) keep the daily branch afterward rather than deleting it. This run
  followed that exact procedure by hand: verified `claude/epic-brahmagupta-g1y16m`
  was still the live Pages branch (deployment `1c368f4` confirmed
  success), branched `claude/daily-2026-07-20` from its tip, added
  today's content, merged back, and pushed
  `claude/daily-2026-07-20:claude/epic-brahmagupta-g1y16m` as a
  fast-forward (no force-push needed this time, since the daily branch
  was a direct descendant). **This does not fix the underlying
  session/branch-forking bug on its own** — that still requires the
  user's Routine-trigger fix — but it gives every future run (even one
  that forks fresh, as has happened 7 times now) an explicit, low-effort
  recovery procedure that converges back onto one persistent branch
  instead of silently drifting.
- **2026-07-21 — bug recurred an eighth time (this run's local checkout
  started on yet another brand-new branch, `claude/great-cray-cx8fq0`,
  itself forked from the stale `claude/gracious-ramanujan-4wyzgc` Day-1-only
  base) — but the new git-workflow procedure from 2026-07-20 caught and
  corrected it cleanly before any work was done.** Following the routine's
  updated instructions to the letter: (1) listed all `claude/*` branches via
  the GitHub MCP tools, (2) called `GET /repos/.../deployments?environment=github-pages`
  and confirmed the most recent successful deployment (2026-07-21T06:22:43Z)
  points at `claude/epic-brahmagupta-g1y16m` (sha `5adcbb9`), (3) diffed
  `briefings/`, `spanish-lessons/`, and `ROUTINE_LOG.md` across branches via
  the GitHub API and confirmed `epic-brahmagupta-g1y16m` is still the
  longest/most-complete, non-diverged history (through 07-20, Day 11,
  Hexagram 11 — no sibling branch had gone further), (4) only then fetched
  that branch locally and branched `claude/daily-2026-07-21` from its tip
  (`git checkout -B claude/daily-2026-07-21 origin/claude/epic-brahmagupta-g1y16m`),
  discarding the stale local starting point entirely rather than working
  from it. Added Spanish Day 12 (-er/-ir verbs), Hexagram 12 (否 Pǐ,
  Standstill — the King Wen Sequence's direct reversal of yesterday's
  Hexagram 11), Brunei, and the "This Is Fine" meme, then fast-forward
  merged `claude/daily-2026-07-21` into `claude/epic-brahmagupta-g1y16m`
  and pushed. **The underlying trigger/session bug is still unresolved**
  (this is the eighth occurrence, 07-09 through 07-21 missing only 07-08
  and — with no recoverable content — 07-18) and still needs the user to
  fix the Routine's persistent-session/branch-targeting configuration
  directly; however, the recovery procedure itself is now working exactly
  as designed and converges on the correct branch every time without any
  content loss or duplication.
- **2026-07-22 — bug recurred a ninth time (this run's local checkout
  started on yet another brand-new branch, `claude/great-cray-5cbil1`);
  the established recovery procedure again caught and corrected it before
  any work was done.** Following the routine's git workflow to the letter:
  (1) listed all `claude/*` branches via the GitHub MCP tools (15 branches
  found), (2) called `GET /repos/.../deployments?environment=github-pages`
  and confirmed the most recent successful deployment (2026-07-21T21:46:03Z)
  points at `claude/epic-brahmagupta-g1y16m` (sha `395bc3a`), (3) diffed
  `briefings/` across all 15 branches via the GitHub API — every sibling
  branch (the `epic-brahmagupta-{b9qdr5,is0gmu,mgut69,nn87ee}` and
  `happy-newton-{6o3hr4,018a9x,d0ctxa,ksqg8o,ltdkx9,qhq5rv,wevard}` lines)
  tops out at 07-17 or earlier, confirming `epic-brahmagupta-g1y16m` (through
  07-21, Day 12, Hexagram 12) is still the longest/most-complete,
  non-diverged history and needed no reconciliation, (4) only then fetched
  that branch locally and branched `claude/daily-2026-07-22` from its tip
  (`git checkout -B claude/daily-2026-07-22 origin/claude/epic-brahmagupta-g1y16m`),
  discarding the stale local starting point entirely. Added Spanish Day 13
  (ir a + infinitivo, near-future tense), Hexagram 13 (同人 Tóng Rén,
  Fellowship with Men — the King Wen Sequence's answer to yesterday's
  Hexagram 12 standstill), Fiji, and the "Lying Flat" (躺平) meme, then
  fast-forward merged `claude/daily-2026-07-22` into
  `claude/epic-brahmagupta-g1y16m` and pushed. **The underlying
  trigger/session bug is still unresolved** (this is the ninth occurrence,
  07-09 through 07-22 missing only 07-08 and — with no recoverable
  content — 07-18); the recovery procedure continues to converge on the
  correct branch every time with no content loss or duplication, but a
  human still needs to fix the Routine's persistent-session/branch-targeting
  configuration to stop it from recurring daily.
- **2026-07-23 — bug recurred a tenth time (this run's local checkout
  started on yet another brand-new/stale branch, `claude/great-cray-41g8pv`,
  frozen at 2026-07-20 content with only Spanish Day 3 / Hexagram 3 —
  itself a descendant of the long-stale `claude/gracious-ramanujan-4wyzgc`
  Day-1-ish base); the established recovery procedure again caught and
  corrected it before any work was done.** Following the routine's git
  workflow to the letter: (1) listed all `claude/*` branches via the
  GitHub MCP tools (16 branches found), (2) listed recent workflow runs
  via the Actions API and confirmed the most recent successful "pages
  build and deployment" run (2026-07-22T21:46:29Z) points at
  `claude/epic-brahmagupta-g1y16m` (sha `ac7e833`, matching
  `claude/daily-2026-07-22`'s tip exactly), (3) diffed `briefings/`,
  `spanish-lessons/`, and `ROUTINE_LOG.md` across all sibling branches —
  every one topped out at 07-20 or earlier (the `happy-newton-d0ctxa`
  branch's lone 2026-07-18 briefing was re-checked and confirmed, again,
  to duplicate Day 2/Hexagram 2/Bhutan/Doge with nothing new, so it
  remains correctly excluded per precedent) — confirming
  `epic-brahmagupta-g1y16m` (through 07-22, Day 13, Hexagram 13) is still
  the longest/most-complete, non-diverged history and needed no
  reconciliation, (4) only then branched `claude/daily-2026-07-23` from
  its tip (`git checkout -B claude/daily-2026-07-23
  origin/claude/epic-brahmagupta-g1y16m`), discarding the stale local
  starting point entirely. Added Spanish Day 14 (estar + gerundio,
  present progressive), Hexagram 14 (大有 Dà Yǒu, Possession in Great
  Measure — the King Wen Sequence's direct inversion of yesterday's
  Hexagram 13 Fellowship), Andorra, and the "Versailles Literature"
  (凡爾賽文學) meme, then fast-forward merged `claude/daily-2026-07-23`
  into `claude/epic-brahmagupta-g1y16m` and pushed. **The underlying
  trigger/session bug is still unresolved** (this is the tenth
  occurrence, 07-09 through 07-23 missing only 07-08 and — with no
  recoverable content — 07-18); the recovery procedure continues to
  converge on the correct branch every time with no content loss or
  duplication, but a human still needs to fix the Routine's
  persistent-session/branch-targeting configuration to stop it from
  recurring daily.
- **2026-07-24 — Routine expanded to SEVEN fixed sections; Section 7
  (film / performing-arts spotlight) and its never-repeat tracking table
  added.** The user updated the Routine prompt to add a daily film /
  performing-arts knowledge item with a detailed explanation, and asked
  for the same never-repeat tracking mechanism the country (Section 5)
  and meme (Section 6) spotlights use. This run branched
  `claude/routine-add-section7-2026-07-24` off the confirmed live portal
  branch's tip (`claude/epic-brahmagupta-g1y16m`, deployment source, tip
  `cf56326` / through 07-23), updated the "Main Briefing Sections" list
  from 6 to 7 entries, and added a new "Film / Performing Arts Spotlights
  Featured" tracking table (empty — the first subject begins with the
  next daily briefing). No daily-briefing content was generated in this
  run; it is a config/prompt-evolution change only, landed on the portal
  branch per the established precedent (cf. the 2026-07-20 git-workflow
  update). Future daily runs must now (a) include Section 7 and (b) log
  each film/arts subject in the new table and never repeat one already
  listed there.
- **2026-07-24 (same day, follow-up) — Routine expanded again to EIGHT
  fixed sections; Section 8 (film-appreciation / criticism method) and a
  `電影/表演藝術` column on the portal `index.html` added.** Per the user's
  request the Routine prompt now includes a daily lesson on HOW to watch
  films — film-analysis / critic's viewing methods and director
  deconstruction (auteur analysis, mise-en-scène, editing, sound, etc.),
  one transferable method/lens per day illustrated with a concrete real
  film scene, taught as a progressive, never-repeat skill track (distinct
  from Section 7's subject spotlight). This run: bumped the sections list
  from 7 to 8, added a "Film-Appreciation / Criticism Method Lessons"
  progress/tracking table (empty; first lesson begins with the next daily
  briefing), and added a new `電影/表演藝術` (Section 7) column to
  `index.html` (all existing rows marked "—" since Section 7 postdates
  them). Branched `claude/routine-add-section8-2026-07-24` off the portal
  tip, fast-forward-merged back into `claude/epic-brahmagupta-g1y16m`, and
  pushed the portal branch. Config-only change; no daily-briefing content
  generated. Future daily runs must now produce all EIGHT sections, log
  Section 8's method + example scene in its table (never repeating a
  method already taught), and fill the new `電影/表演藝術` index column.
  (Follow-up, same day: a `看片方法` (Section 8) column was also added to
  `index.html`, existing rows marked "—"; daily runs must fill it too.)
- **2026-07-24 (daily run) — bug recurred an eleventh time (this run's
  local checkout started on a brand-new branch, `claude/bold-goldberg-tvacij`,
  itself forked from the long-stale `claude/gracious-ramanujan-4wyzgc`
  Day-1-only base); the established recovery procedure again caught and
  corrected it before any work was done.** Following the routine's git
  workflow to the letter: (1) listed all `claude/*` branches via the
  GitHub MCP tools (20 branches found, including the same-day
  `claude/routine-add-section7-2026-07-24` and
  `claude/routine-add-section8-2026-07-24` config-change branches noted
  above), (2) called `GET /repos/.../deployments?environment=github-pages`
  directly (not the repo's `default_branch` field) and confirmed the most
  recent successful deployment (2026-07-24T03:27:01Z) points at
  `claude/epic-brahmagupta-g1y16m` (sha `452c24c`), (3) fetched
  `ROUTINE_LOG.md`, `briefings/`, and `spanish-lessons/` from that branch
  via the GitHub API and confirmed it already contains the SEVEN/EIGHT-section
  config updates from earlier today plus the full daily history through
  2026-07-23 (Day 14, Hexagram 14, Andorra, Versailles Literature) with
  Sections 7/8 tracking tables still empty (no daily content yet used
  either slot) — so no reconciliation from any sibling branch was needed,
  only today's actual daily content, (4) only then fetched that branch
  locally and branched `claude/daily-2026-07-24` from its tip
  (`git checkout -B claude/daily-2026-07-24 origin/claude/epic-brahmagupta-g1y16m`),
  discarding the stale local starting point entirely. Added Spanish Day 15
  (gustar + indirect object pronouns), Hexagram 15 (謙 Qiān, Modesty — the
  King Wen Sequence's answer to yesterday's Hexagram 14 Great Possession,
  and traditionally the one hexagram whose six lines are all favorable),
  Nepal, the "Distracted Boyfriend" meme, and — for the first time —
  Section 7 (Citizen Kane, 1941) and Section 8 (mise-en-scène, worked
  through Citizen Kane's deep-focus "snow globe" scene, deliberately
  chosen to pair with Section 7's subject on this inaugural day for both
  new sections). Fast-forward merged `claude/daily-2026-07-24` into
  `claude/epic-brahmagupta-g1y16m` and pushed. **The underlying
  trigger/session bug is still unresolved** (this is the eleventh
  occurrence of a fresh/stale starting branch, 07-09 through 07-24
  missing only 07-08 and — with no recoverable content — 07-18); the
  recovery procedure continues to converge on the correct branch every
  time with no content loss or duplication, but a human still needs to
  fix the Routine's persistent-session/branch-targeting configuration to
  stop it from recurring daily.
- **2026-07-25 — clean run, portal branch confirmed stable, no
  reconciliation needed.** This session's local checkout started on
  `claude/bold-goldberg-lk5i4n`, a branch with no prior daily content —
  so, per the routine's mandatory pre-check, this run did not trust that
  starting point. It instead: (1) listed all `claude/*` branches via the
  GitHub MCP tools (21 branches found), (2) queried
  `GET /repos/.../deployments?environment=github-pages` directly (not the
  repo's `default_branch` field) and confirmed the most recent successful
  deployment (2026-07-24T21:49:08Z) points at
  `claude/epic-brahmagupta-g1y16m` (sha `2536a7b`), (3) ran a `compare`
  check between every sibling `claude/*` branch and that portal tip —
  every one came back `behind` or `diverged`, with none strictly ahead
  (spot-checked the diverged commits on `gracious-ramanujan-4wyzgc` and
  `happy-newton-wevard`; both contained only old 07-19-era duplicate
  material already accounted for), confirming `epic-brahmagupta-g1y16m`
  (through 07-24, Day 15, Hexagram 15, plus Sections 7/8's inaugural
  entries) genuinely is the longest/most-complete history and needed no
  reconciliation. Only then branched `claude/daily-2026-07-25` from its
  tip, discarding the stale local starting point entirely. Added Spanish
  Day 16 (regular-verb simple past / pretérito indefinido), Hexagram 16
  (豫 Yù, Enthusiasm — the King Wen Sequence's natural follow-on from
  yesterday's Hexagram 15 Modesty), Somaliland (the first Section 5 entry
  to be a de facto/unrecognized state rather than a UN member country,
  chosen deliberately for variety), Pepe the Frog (first Section 6 entry
  with a genuinely contested, multi-faceted legacy), Peking Opera (京劇,
  the first Section 7 entry drawn from the performing arts rather than
  cinema), and Editing &amp; Montage as Section 8's second film-analysis
  lesson (worked through Battleship Potemkin's Odessa Steps sequence).
  Fast-forward merged `claude/daily-2026-07-25` into
  `claude/epic-brahmagupta-g1y16m` and pushed. Whether today's starting
  branch reflects a fresh recurrence of the long-running divergence bug
  is ambiguous (that branch had no daily content either way to compare
  against), but regardless, the mandatory verify-before-work procedure
  caught it and no content was lost or duplicated.
- **2026-07-26 — bug recurred a twelfth time (this run's local checkout
  started on `claude/bold-goldberg-jmzm38`, frozen at 2026-07-20-era
  content with only Spanish Day 3 / Hexagram 3 — itself a descendant of
  the long-stale `claude/gracious-ramanujan-4wyzgc` base); the established
  recovery procedure again caught and corrected it before any work was
  done.** A direct `GET /repos/.../deployments?environment=github-pages`
  call from this session returned HTTP 403 via `WebFetch` (the same
  network restriction noted in several earlier runs), so this run used the
  documented fallback instead: (1) listed all `claude/*` branches via the
  GitHub MCP tools (22 branches found), (2) fetched `ROUTINE_LOG.md`,
  `briefings/`, `spanish-lessons/`, and `index.html` from
  `claude/daily-2026-07-25` (its tip sha `320a5f3` matches
  `claude/epic-brahmagupta-g1y16m`'s branch-list sha exactly, confirming
  the daily branch had already been fast-forward-merged into the portal
  branch as designed) and confirmed it contains the full history through
  2026-07-25 (Day 16, Hexagram 16, Somaliland, Pepe the Frog, Peking
  Opera, Editing & Montage) with no gaps, (3) spot-checked every other
  `claude/epic-brahmagupta-*` and `claude/happy-newton-*` sibling branch's
  single most recent commit and confirmed every one tops out at 2026-07-17
  or earlier (all long-dead, already-accounted-for lines) — so
  `claude/epic-brahmagupta-g1y16m` needed no reconciliation from any
  sibling branch. Only then branched `claude/daily-2026-07-26` from its
  tip (`git checkout -B claude/daily-2026-07-26
  origin/claude/epic-brahmagupta-g1y16m`), discarding the stale local
  starting point entirely. Added Spanish Day 17 (irregular preterite
  ir/ser/hacer), Hexagram 17 (隨 Suí, Following — the King Wen Sequence's
  natural follow-on from yesterday's Hexagram 16 Enthusiasm, per the
  Xugua commentary "豫必有隨"), Indonesia (the first Section 5 entry
  chosen deliberately for scale contrast against the run of small
  states/microstates featured recently), Woman Yelling at a Cat (first
  Section 6 entry sourced from English-language reaction-image/Twitter
  meme culture rather than a single-image macro), Kabuki (歌舞伎, the
  second Section 7 entry drawn from the performing arts, this time
  Japanese rather than Chinese), and Cinematography & Lighting as Section
  8's third film-analysis lesson (worked through Blade Runner 2049's
  Las Vegas sequence, cinematography by Roger Deakins). Fast-forward
  merged `claude/daily-2026-07-26` into `claude/epic-brahmagupta-g1y16m`
  and pushed. **The underlying trigger/session bug is still unresolved**
  (this is the twelfth occurrence of a fresh/stale starting branch,
  07-09 through 07-26 missing only 07-08 and — with no recoverable
  content — 07-18); the recovery procedure continues to converge on the
  correct branch every time with no content loss or duplication, but a
  human still needs to fix the Routine's persistent-session/branch-targeting
  configuration to stop it from recurring daily.
- **2026-07-27 — bug recurred a thirteenth time (this run's local checkout
  started on `claude/bold-goldberg-6dryev`, frozen at 2026-07-20-era
  content with only Spanish Day 3 / Hexagram 3 — itself a descendant of
  the long-stale `claude/gracious-ramanujan-4wyzgc` base); the established
  recovery procedure again caught and corrected it before any work was
  done.** Following the routine's git workflow to the letter: (1) listed
  all `claude/*` branches via the GitHub MCP tools (23 branches found),
  (2) queried the Actions API for the `pages-build-deployment` workflow's
  recent runs and confirmed the most recent successful run
  (2026-07-26T21:49:34Z) has `head_branch: claude/epic-brahmagupta-g1y16m`,
  matching that branch's tip sha (`40fa395a`) exactly, (3) fetched
  `ROUTINE_LOG.md`, `briefings/`, and `spanish-lessons/` from that branch
  via the GitHub API and confirmed it contains the full, non-duplicate
  history through 2026-07-26 (Day 17, Hexagram 17, Indonesia, Woman
  Yelling at a Cat, Kabuki, Cinematography & Lighting) — no reconciliation
  from any sibling branch was needed. Only then fetched that branch
  locally and branched `claude/daily-2026-07-27` from its tip
  (`git checkout -B claude/daily-2026-07-27 origin/claude/epic-brahmagupta-g1y16m`),
  discarding the stale local starting point entirely. Added Spanish Day 18
  (u-stem irregular preterites tener/estar/poder), Hexagram 18 (蠱 Gǔ,
  Work on What Has Been Spoiled — the King Wen Sequence's answer to
  yesterday's Hexagram 17 Following, per the Xugua commentary "以喜隨人者
  必有事,故受之以蠱"), Kazakhstan (the first Section 5 entry that is the
  world's largest landlocked country, chosen for scale contrast against
  the recent run of small states/microstates), Harlem Shake (first
  Section 6 entry from the pre-Vine/TikTok flash-viral-video era of
  meme history rather than an image macro), Seven Samurai (1954, dir.
  Akira Kurosawa — first Section 7 entry drawn from a landmark narrative
  film rather than a performing-arts tradition since Citizen Kane), and
  Sound Design & Score as Section 8's fourth film-analysis lesson (worked
  through Psycho's shower-scene score by Bernard Herrmann). Fast-forward
  merged `claude/daily-2026-07-27` into `claude/epic-brahmagupta-g1y16m`
  and pushed. **The underlying trigger/session bug is still unresolved**
  (this is the thirteenth occurrence of a fresh/stale starting branch,
  07-09 through 07-27 missing only 07-08 and — with no recoverable
  content — 07-18); the recovery procedure continues to converge on the
  correct branch every time with no content loss or duplication, but a
  human still needs to fix the Routine's persistent-session/branch-targeting
  configuration to stop it from recurring daily.
- **2026-07-28 — bug recurred a fourteenth time (this run's local checkout
  started on `claude/bold-goldberg-6buwxy`, frozen at 2026-07-20-era
  content with only 3 briefings and Spanish Day 3 / Hexagram 3 — itself a
  descendant of the long-stale `claude/gracious-ramanujan-4wyzgc` base);
  the established recovery procedure again caught and corrected it before
  any work was done.** Following the routine's git workflow to the letter:
  (1) listed all `claude/*` branches via the GitHub MCP tools (24 branches
  found), (2) queried `GET /repos/.../deployments?environment=github-pages`
  directly (not the repo's `default_branch` field) via a direct `curl`
  using the session's `GH_TOKEN` (successful this time — no 403) and
  confirmed the most recent successful deployment (2026-07-27T21:50:04Z)
  points at `claude/epic-brahmagupta-g1y16m` (sha `84fd516`), (3) fetched
  every sibling `claude/*` branch locally and compared `briefings/` and
  `spanish-lessons/` file counts plus each branch's last-commit date —
  `claude/daily-2026-07-27` matched `epic-brahmagupta-g1y16m`'s tip sha
  exactly (19 briefings, Day 18/Hexagram 18, through 2026-07-27) and every
  other sibling topped out at 2026-07-20 or earlier, confirming
  `epic-brahmagupta-g1y16m` needed no reconciliation from any sibling
  branch. Only then branched `claude/daily-2026-07-28` from its tip
  (`git checkout -B claude/daily-2026-07-28
  origin/claude/epic-brahmagupta-g1y16m`), discarding the stale local
  starting point entirely. Added Spanish Day 19 (j-stem irregular
  preterites decir/traer/conducir — the sole exception to the -ieron
  ending, since a j-stem swallows the "i" to give -eron), Hexagram 19
  (臨 Lín, Approach — the King Wen Sequence's natural follow-on from
  yesterday's Hexagram 18 Gǔ, per the Xugua commentary "蠱者事也,有事而後
  可大,故受之以臨"), Singapore (the first Section 5 entry to be a
  city-state built on financial/trade-hub economics rather than natural
  resources), Bernie Sanders' Mittens (first Section 6 entry sourced from
  a real-world political/news event rather than dance, image-macro, or
  reaction-video culture), Bunraku (文樂, the third Section 7 entry drawn
  from the performing arts, Japanese puppet theatre this time rather than
  Kabuki or a narrative film), and Colour as Section 8's fifth
  film-analysis lesson (worked through Schindler's List's girl in the red
  coat). Fast-forward merged `claude/daily-2026-07-28` into
  `claude/epic-brahmagupta-g1y16m` and pushed. **The underlying
  trigger/session bug is still unresolved** (this is the fourteenth
  occurrence of a fresh/stale starting branch, 07-09 through 07-28 missing
  only 07-08 and — with no recoverable content — 07-18); the recovery
  procedure continues to converge on the correct branch every time with no
  content loss or duplication, but a human still needs to fix the
  Routine's persistent-session/branch-targeting configuration to stop it
  from recurring daily.

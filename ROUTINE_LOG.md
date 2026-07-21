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

## Main Briefing Sections (fixed, 6 total per day)

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

## Internet Meme Spotlights Featured

| Date | Meme |
|------|------|
| 2026-07-14 | Rickroll (瑞克搖) |
| 2026-07-15 | "8+9" (八加九, Taiwan) |
| 2026-07-16 | Gangnam Style (江南 Style, South Korea) |
| 2026-07-17 | Doge (狗狗迷因) |
| 2026-07-19 | Skibidi Toilet (滑稽馬桶) |
| 2026-07-20 | "Ohio" / "Only in Ohio" |

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

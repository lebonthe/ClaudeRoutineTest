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
- **STEP 0 — verify the actual current date before deciding anything
  (established 2026-08-27, after the exact opposite mistake happened on
  both 2026-08-26 and 2026-08-27).** Before touching git at all — before
  even the branch-recovery steps below — read the session's own
  current-date context (or the system clock) directly. Do NOT infer
  "today" from the portal branch's most recent dated entry, from a daily
  branch's name, or from an assumption that the previous run must have
  covered "yesterday": the portal branch's latest entry is only a LOWER
  BOUND on progress, never a substitute for checking the real date.
  Compute `days_owed = (actual current date) − (portal branch's latest
  dated entry)`. If `days_owed ≥ 1`, today's content still needs to be
  produced, dated as the actual current date — not skipped because the
  portal branch "looks recent." Only if `days_owed = 0` **after this
  arithmetic** (never after just eyeballing dates) is it a genuine
  duplicate same-day firing; log it in Run Notes and stand down without
  advancing any of the six never-repeat sequences. Do this every single
  run, even when the portal branch looks freshly updated — that is
  exactly the condition under which the shortcut becomes tempting and
  wrong.
- **Market data must be for the actual current date, verified fresh, not
  reused or mislabeled (established 2026-08-27).** When researching
  Section 1, always search using the actual current date from the STEP 0
  check above, never a guessed/previous date or figures remembered from
  an earlier run. Independently compute the weekday of the actual current
  date yourself and use it to determine which trading session is genuinely
  the most recently closed one relative to the current Taipei generation
  time — do not trust a search result's own date label at face value;
  search summaries have repeatedly returned a prior session's figures
  under the wrong date. When multiple queries return different numbers
  for what should be the same session, treat that as a sign of a
  stale/mislabeled result, not normal noise — re-query with session-
  specific context (named same-day events, companies, data releases) to
  confirm the correct day's figures before writing them into the
  briefing, and prefer a sourced, internally consistent account over a
  bare unverified number. If genuinely current data cannot be confirmed
  for a given market, say so explicitly in that bullet rather than
  presenting stale or unverified figures as current.

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
| 2026-07-29 | 20 | 過去未完成式入門(Pretérito Imperfecto) | Regular imperfect endings: -ar verbs take -aba/-abas/-aba/-ábamos/-aban; -er/-ir verbs share -ía/-ías/-ía/-íamos/-ían; only three irregular verbs in the whole tense (ser→era, ir→iba, ver→veía); contrasted with the preterite (completed single event) vs. imperfect (ongoing/habitual/background state) | spanish-lessons/day-20.html |
| 2026-07-30 | 21 | 現在完成式入門(Pretérito Perfecto Compuesto) | Spanish's first compound tense: auxiliary haber (he/has/ha/hemos/han) + past participle (-ado/-ido, plus irregulars like hecho/dicho/escrito/visto/puesto/vuelto); used for past actions still tied to the present (hoy, esta semana, alguna vez, todavía no), contrasted with the closed-off simple past (ayer) | spanish-lessons/day-21.html |
| 2026-07-31 | 22 | 過去完成式入門(Pretérito Pluscuamperfecto) | Second compound tense: haber's imperfect forms (había/habías/había/habíamos/habían) + the same past participles taught on Day 21; marks an action completed before another, more recent past-tense reference point ("the past of the past"), directly parallel to English "had done" | spanish-lessons/day-22.html |
| 2026-08-01 | 23 | 未來簡單式入門(Futuro Simple) | First future tense: regular verbs add one shared ending set (-é/-ás/-á/-emos/-án) directly onto the full infinitive (not a shortened stem) across all three verb families; 12 common verbs use an irregular stem (e-dropping: podr-/sabr-/querr-/habr-; d-insertion: tendr-/pondr-/saldr-/vendr-; shortened: har-/dir-) but keep the identical endings; also usable for present-tense probability/conjecture ("¿Qué hora será?") | spanish-lessons/day-23.html |
| 2026-08-02 | 24 | 條件式簡單式入門(Condicional Simple) | The "twin" of Day 23's future tense: regular verbs take the identical full-infinitive formation but with endings -ía/-ías/-ía/-íamos/-ían; reuses the exact same 12 irregular stems taught for the future tense (podr-/sabr-/querr-/habr-/tendr-/pondr-/saldr-/vendr-/har-/dir-); four core uses — hypothetical "would," polite requests (Me gustaría..., ¿Podrías...?), reported "future" inside past-tense speech (dijo que vendría), and conjecture about the past (¿Qué hora sería?) | spanish-lessons/day-24.html |
| 2026-08-03 | 25 | 祈使語氣肯定命令式入門(El Imperativo Afirmativo) | First shift from tense to mood: regular tú commands borrow the él/ella present-tense form (habla/come/escribe) with zero new conjugation; regular usted commands use the "opposite vowel" pattern (-ar→-e: hable; -er/-ir→-a: coma/escriba), the same pattern later reused by the present subjunctive; eight irregular tú commands must be memorized as a set: di/haz/ve/pon/sal/sé/ten/ven (decir/hacer/ir/poner/salir/ser/tener/venir) | spanish-lessons/day-25.html |
| 2026-08-04 | 26 | 祈使語氣否定命令式(El Imperativo Negativo) | Unlike affirmative commands, ALL negative commands (tú and usted alike) borrow the present subjunctive form; regular usted negative commands look identical to affirmative usted commands (no hable/coma/escriba), but regular tú negative commands are brand-new forms that must NOT reuse the affirmative tú command (no hables/comas/escribas, not "no habla/come/escribe"); the eight affirmative-irregular tú commands (di/haz/ve/pon/sal/sé/ten/ven) are replaced by subjunctive forms built from the irregular yo-stem (no digas/hagas/pongas/salgas/tengas/vengas), with ir/ser as the two true exceptions (no vayas/seas); object/reflexive pronouns also flip from after the verb (affirmative) to before it (negative) | spanish-lessons/day-26.html |
| 2026-08-05 | 27 | 虛擬式現在式入門(El Presente de Subjuntivo) | The mood underlying Days 25-26's commands, formally named and generalized: regular verbs take the same "opposite vowel" endings already seen in commands (-ar→-e/-es/-e/-emos/-en; -er/-ir→-a/-as/-a/-amos/-an), with yo and él/ella always identical (unlike the indicative); any indicative irregular yo-stem (tengo, hago) carries through every subjunctive person; first use taught: querer/esperar que + subjunctive to express a wish about a *different* subject's action, contrasted with querer + infinitive when wisher and doer are the same person | spanish-lessons/day-27.html |
| 2026-08-06 | 28 | 虛擬式現在式:懷疑、否定與非人稱表達(El Subjuntivo con Duda, Negación y Expresiones Impersonales) | Second major subjunctive trigger family: creer que + indicative when affirmative but no creer que + subjunctive when negated (same flip for es/no es cierto-verdad que); dudar que takes the subjunctive in both affirmative and negative form since doubt itself is inherently uncertain; impersonal es posible/probable que + subjunctive; colloquial exception flagged: a lo mejor ("maybe") conventionally takes the *indicative* despite meaning almost the same as es posible que | spanish-lessons/day-28.html |
| 2026-08-07 | 29 | 虛擬式現在式:情感表達(El Subjuntivo con Expresiones de Emoción) | Third major subjunctive trigger family (emotion), which works on different logic than Day 28's doubt: alegrarse de que, sentir que, sorprender, es una lástima que, and temer que all take the subjunctive even when the embedded clause is a fact the speaker is fully certain of, because the subjunctive here marks emotional commentary/reaction rather than new asserted information; sorprender/encantar/molestar reuse Day 15's "backwards" gustar-pattern grammar; introduced the WEIRDO mnemonic (Wishes/Emotions/Impersonal/Recommendations/Doubt/Ojalá) to frame Days 27-29 within the larger subjunctive-trigger taxonomy | spanish-lessons/day-29.html |
| 2026-08-08 | 30 | 虛擬式現在式:建議、請求與必要性表達(El Subjuntivo con Recomendaciones, Peticiones y Necesidad) | Fourth major subjunctive trigger family (recommendations/requests, plus impersonal necessity): recomendar/sugerir/pedir/exigir que share Day 27's two-subject structure but mark active influence over another's behavior rather than a mere wish; es necesario/importante que extends Day 28's impersonal-expression category from possibility to necessity; sharpest trap is decir que, which takes the indicative when reporting a fact (Le digo que viene) but the subjunctive when giving an order (Le digo que venga), since it then functions as pedir; WEIRDO mnemonic now covers five of six categories (W/E/I/R/D), leaving only Ojalá for a future lesson | spanish-lessons/day-30.html |
| 2026-08-09 | 31 | 虛擬式現在式:Ojalá(但願、希望) | Completes the WEIRDO mnemonic's sixth and final letter: Ojalá (from Arabic "law shā' allāh" via ~800 years of Moorish presence in Iberia) is a fixed, non-conjugating exclamation (unlike every other WEIRDO trigger) always followed by the subjunctive, usable for wishes about oneself, others, or uncontrollable events (weather); que is optional; flagged (not yet taught) that swapping in the imperfect subjunctive lets the same word pivot from a hopeful future wish (Ojalá llueva) to a wistful counterfactual one (Ojalá lloviera) | spanish-lessons/day-31.html |
| 2026-08-10 | 32 | 虛擬式現在式:時間副詞子句(El Subjuntivo en Cláusulas Adverbiales de Tiempo) | First major subjunctive trigger category outside WEIRDO: cuando/en cuanto/tan pronto como/hasta que take the subjunctive when the clause describes a still-pending future action but the indicative when describing a habitual or already-completed one; antes de que is the sole exception, always taking the subjunctive in every tense since "before X" inherently frames X as not-yet-real; this category marks objective time-relative-to-speech rather than WEIRDO's subjective attitude | spanish-lessons/day-32.html |
| 2026-08-11 | 33 | 虛擬式現在式:形容詞子句(El Subjuntivo en Cláusulas Adjetivas / Relativas) | Second major subjunctive trigger category outside WEIRDO, independent from Day 32's time clauses: adjective/relative clauses take the subjunctive when the antecedent (the noun described) is indefinite, hypothetical, or explicitly nonexistent (busco un apartamento que tenga..., no conozco a nadie que hable...), but the indicative when the antecedent is a specific, known-to-exist thing or person (vivo en un apartamento que tiene...); a third independent axis for choosing subjunctive vs. indicative, alongside WEIRDO's subjective attitude and Day 32's objective time-relative-to-speech | spanish-lessons/day-33.html |
| 2026-08-12 | 34 | 虛擬式現在式:目的與讓步副詞子句(El Subjuntivo en Cláusulas Adverbiales de Propósito y Concesión) | Third major subjunctive trigger category outside WEIRDO: para que + subjunctive marks purpose only when the purpose clause's subject differs from the main clause's (same-subject purpose uses para + infinitive instead); aunque is the single connector able to take either mood, subjunctive when the conceded fact is still hypothetical/unconfirmed (aunque llueva) vs. indicative when the speaker already knows it to be true (aunque llueve) — the sharpest "trap" in the whole subjunctive system; a menos que/con tal de que/sin que behave like Day 32's antes de que, taking only the subjunctive in every case with no indicative alternative | spanish-lessons/day-34.html |
| 2026-08-13 | 35 | 虛擬式過去未完了式入門(El Pretérito Imperfecto de Subjuntivo) | Delivers the tense Day 31 flagged but didn't teach: formed by taking any verb's preterite "ellos" form (Days 16-19), dropping -ron, and adding -ra/-ras/-ra/-ramos/-ran (an equivalent -se family also exists) — inherits preterite irregularities rather than introducing new ones (tuvieron→tuviera, dijeron→dijera, fueron→fuera); three uses taught: Ojalá + imperfect subjunctive for wistful/contrary-to-fact present wishes (Ojalá lloviera, vs. Day 31's hopeful Ojalá llueva), a first preview of "Si + imperfect subjunctive, + conditional" contrary-to-present-fact conditionals, and sequence-of-tenses (a past-tense WEIRDO trigger pulls its subjunctive clause back to the imperfect subjunctive: quería que estudiáramos) | spanish-lessons/day-35.html |
| 2026-08-14 | 36 | 與現在事實相反的條件句(Oraciones Condicionales — Si + Imperfecto de Subjuntivo + Condicional) | Formalizes the pattern Day 35 only previewed: Type 2 (contrary-to-present-fact) conditional sentences fix each clause's tense in one direction only — the si-clause always takes Day 35's imperfect subjunctive (si tuviera, never si tendría or si tenga) and the result clause always takes Day 24's conditional simple (aprendería, never aprendiera); clause order is reversible with a comma only when the si-clause comes first; contrasted with the "real/likely" Type 1 conditional (si + present indicative + present/future/imperative) reserved for a future lesson | spanish-lessons/day-36.html |
| 2026-08-15 | 37 | 與現在事實/未來相符的條件句(Oraciones Condicionales — Si + Presente de Indicativo + Presente/Futuro/Imperativo) | Delivers the "real/likely" Type 1 conditional Day 36 flagged: the si-clause always takes the present indicative (si tienes, never si tengas or si tuvieras) while the result clause can take the present indicative (general rule), future simple (Day 23, one-time promise), or imperative (Day 25/26, direct advice); completes the two-conditional-type contrast with Day 36 (present indicative + 3 possible moods vs. imperfect subjunctive + conditional simple only) and warns against blending the two systems' tenses | spanish-lessons/day-37.html |
| 2026-08-17 | 38 | 與過去事實相反的條件句(Oraciones Condicionales — Si + Pluscuamperfecto de Subjuntivo + Condicional Compuesto) | Completes the three-type conditional trilogy begun on Days 36-37: the "contrary-to-past-fact" Type 3 conditional promotes both of Type 2's simple tenses one level into haber-based compound tenses — the si-clause takes the pluperfect subjunctive (hubiera/hubieras/hubiera/hubiéramos/hubieran, Day 35's imperfect-subjunctive stem applied to haber, + Day 21's past participle) and the result clause takes the conditional perfect (habría/habrías/habría/habríamos/habrían, Day 24's conditional-simple stem applied to haber, + the same participle); used to imagine a different outcome for an already-finished, unchangeable past event, distinct from Type 2's present-tense hypothetical and Type 1's open future | spanish-lessons/day-38.html |
| 2026-08-18 | 39 | 未來完成式(Futuro Perfecto / Futuro Compuesto) | Completes the "haber + past participle" compound-tense square begun on Days 21-22 and continued on Day 38: formed from haber's own future-simple stem (habr-, one of Day 23's twelve irregular future stems) + Day 21's past participle (habré/habrás/habrá/habremos/habrán + participio); marks either a future-anterior action already completed by a given future reference point (often with para + time or a Day-32 cuando + present-subjunctive clause) or a conjecture about something already completed (¿Habrá llegado ya?), extending the conjecture pattern from Day 23's future simple (present conjecture) and Day 24's conditional simple (past conjecture) one step further | spanish-lessons/day-39.html |
| 2026-08-19 | 40 | 虛擬式現在完成式(El Pretérito Perfecto de Subjuntivo) | Gives the subjunctive mood its own compound-tense partner, mirroring Day 39's indicative/conditional square: formed from haber's present-subjunctive stem (haya/hayas/haya/hayamos/hayáis/hayan) + Day 21's past participle; takes exactly the same WEIRDO trigger vocabulary taught across Days 27-34, but marks an action already completed relative to the present (Espero que hayas dormido bien) rather than one happening now or later (Espero que duermas bien); pairs with Day 27's presente de subjuntivo the same way Day 35's imperfecto de subjuntivo pairs with the pluscuamperfecto de subjuntivo already used inside Day 38's contrary-to-past-fact "si" clauses | spanish-lessons/day-40.html |
| 2026-08-20 | 41 | Como si + Imperfecto/Pluscuamperfecto de Subjuntivo(彷彿……一樣) | A new fixed trigger phrase, distinct from any clause-type category taught so far: como si ("as if") always takes the subjunctive, never the indicative, since it inherently compares reality to something admittedly untrue; it reuses two already-taught tenses depending on timing rather than introducing new conjugation — Day 35's imperfect subjunctive (fuera, conociera) for a same-time unreal comparison, or Day 38's pluperfect subjunctive (hubiera pasado) for a comparison about something supposedly already finished | spanish-lessons/day-41.html |
| 2026-08-21 | 42 | 比較句與最高級(Comparativos y Superlativos) | Deliberately steps outside verb conjugation into a new grammar area: unequal comparison más/menos + adjective + que, equal comparison tan + adjective + como, and the superlative el/la/los/las + más/menos + adjective + de (never en); irregular comparatives bueno/malo→mejor/peor and age-sense grande/pequeño→mayor/menor must be memorized rather than built with más/menos, while size-sense grande/pequeño keep the regular más grande/más pequeño form | spanish-lessons/day-42.html |
| 2026-08-22 | 43 | 絕對最高級(El Superlativo Absoluto: -ísimo) | Continues Day 42's comparison/ranking area with its complement: the absolute superlative suffix -ísimo/-ísima intensifies an adjective ("extremely X") with no comparison group at all, distinct from Day 42's relative superlative (el/la más...de, which ranks within a named group); formed by dropping the final vowel and adding -ísimo/-ísima, with three spelling adjustments to preserve consonant sound (-co/-ca→-quísimo, -go/-ga→-guísimo, -z→-císimo); contrasted in register with plain muy + adjective (more neutral/everyday than the more emphatic, colloquial -ísimo, and the two are not normally stacked) | spanish-lessons/day-43.html |
| 2026-08-23 | 44 | 直接受詞代名詞(Los Pronombres de Objeto Directo: lo/la/los/las) | Steps outside the tense/mood track to fill a foundational gap: direct object pronouns lo/la/los/las replace a noun directly receiving a verb's action, agreeing in gender/number with the replaced noun rather than the speaker (el libro→lo, la llave→la, los libros→los, las llaves→las); placed before a conjugated verb (Lo tengo) or, with an infinitive/gerund (Day 13's ir a, Day 14's present progressive), either before the verb group or attached to the infinitive/gerund's end (Voy a comprarlas, Estoy comprándolas — the latter requiring an accent to preserve stress); directly contrasted with Day 15's indirect object pronouns, which share me/te/nos but diverge in the third person (indirect le/les ignores gender; direct lo/la/los/las must match it, even for people, unlike the regional Spain-only leísmo variant) | spanish-lessons/day-44.html |
| 2026-08-24 | 45 | 直接與間接受詞代名詞合併使用(Los Pronombres de Objeto Directo e Indirecto Combinados) | Combines Day 15's indirect object pronouns (me/te/le/nos/les) with Day 44's direct object pronouns (lo/la/los/las) into one sentence: fixed word order always places indirect before direct (Me lo das, Te la compro, Nos los envían); a third-person indirect pronoun (le/les) is obligatorily replaced by se whenever it precedes a third-person direct pronoun, to avoid the disallowed "le lo"/"les la" sequence (Se lo doy, never Le lo doy), with a clarifying a él/a ella/a usted phrase added when se's ambiguity matters; both pronouns must move together as one unit under the same before-conjugated-verb / attached-to-infinitive-or-gerund placement rules already learned, never split apart (Te lo voy a dar / Voy a dártelo, never "Te voy a lo dar") | spanish-lessons/day-45.html |
| 2026-08-26 | 46 | 反身動詞與反身代名詞(Los Verbos Reflexivos y los Pronombres Reflexivos) | Formalizes the reflexive pronoun system (me/te/se/nos/os/se) silently used since Day 1's Me llamo; regular reflexive verbs (levantarse, ducharse, vestirse, acostarse) conjugate normally with a matching reflexive pronoun before the conjugated verb or attached to an infinitive/gerund/affirmative command, same placement rules as Days 44-45; deliberately sequenced right after Day 45 to contrast identical spelling with opposite function — yesterday's se is a forced le/les→se substitution before a third-person direct object pronoun (two participants), today's se is a true reflexive pronoun where subject acts on itself (one participant, no accompanying lo/la/los/las) | spanish-lessons/day-46.html |
| 2026-08-27 | 47 | 相互動詞(Los Verbos Recíprocos) | Extends Day 46's reflexive pronouns (me/te/se/nos/os/se) to their second, distinct function: reciprocal "each other" meaning, possible only with a plural subject (nosotros/vosotros/ellos-ellas-ustedes) and a verb whose meaning logically allows a two-way exchange (verse, quererse, ayudarse, abrazarse, escribirse); identical spelling to the reflexive use means a sentence like Se abrazan is genuinely ambiguous in isolation (reflexive "they hug themselves" vs. reciprocal "they hug each other"), resolved when needed with el uno al otro/la una a la otra (two people) or los unos a los otros/unas a otras (larger groups); not every plural reflexive-shaped verb admits a reciprocal reading at all — dormirse ("fall asleep") has no two-way meaning to borrow, so nos dormimos can only mean "we fell asleep," never a reciprocal action | spanish-lessons/day-47.html |
| 2026-08-28 | 48 | 無人稱與被動 se(El Se Impersonal y la Voz Pasiva Refleja) | Gives se its third and final identity, distinct from Day 46's reflexive (subject acts on itself) and Day 47's reciprocal (subjects act on each other): a construction with no identifiable agent at all, splitting into two rules despite identical spelling — impersonal se pairs with a verb that has no concrete noun to serve as grammatical subject and stays fixed in the third-person singular regardless of how many people are implied (Se vive bien aquí, Se dice que...), while passive se (voz pasiva refleja) promotes the thing acted upon into the grammatical subject, so the verb must agree with it in number (Se vende casa vs. Se venden casas); flagged edge case: when the sought object is a specific person marked with the personal "a" (Se busca a los voluntarios), it falls under impersonal se + direct object rather than passive se, since a personal-a-marked noun cannot itself be a grammatical subject, and prescriptive usage often keeps the verb singular even when plural people are meant | spanish-lessons/day-48.html |
| 2026-08-29 | 49 | 以 ser 構成的被動語態(La Voz Pasiva con "Ser") | Delivers the classic "textbook" passive that Day 48's se-passive was always contrasted against — ser (any tense) + past participle agreeing in gender/number with the subject + optional por + agent — the one structural power the se-passive can never offer, since se-passive sentences (Se vende la casa) cannot name who performed the action while the ser-passive can (La casa fue vendida por un banco); because everyday speech overwhelmingly prefers the active voice or se-passive, the ser-passive concentrates in formal writing/news/historical-legal narration, registers where naming a specific agent actually matters; sharpest contrast with every haber-based compound tense (Days 21, 22, 38, 39, 40): haber's past participle never changes form, but the ser-passive's past participle behaves like an adjective and must agree with the subject in gender and number (fue construido/construida, fueron construidos/construidas) | spanish-lessons/day-49.html |
| 2026-08-30 | 50 | estar + 過去分詞的結果狀態(El Estado Resultante con "Estar") | The direct pair to Day 49's ser-passive: estar (any tense) + past participle (still agreeing in gender/number with the subject, same rule as Day 49) describes the resulting state/condition left behind by a prior action rather than the action/event itself (La ventana está rota = it's broken, a state, vs. Day 49's La ventana fue rota por el niño = the event of breaking it, with a named agent); estar+participle can never take a "por + agente" phrase the way ser-passive can, since it isn't narrating an action at all; far more common in everyday speech than Day 49's ser-passive, since describing a thing's current condition is a constant daily need | spanish-lessons/day-50.html |
| 2026-08-31 | 51 | Por 與 Para 的用法區分(Por vs. Para) | Steps outside the tense/mood track entirely to resolve Spanish learners' most notorious point of confusion: por points backward to a cause/reason, duration, route travelled through, or exchange/price (por tu cumpleaños, por una hora, por el centro), while para points forward to a purpose (para + infinitive), recipient, deadline, or destination (para ti, para comprarlo, para el viernes, para Madrid); the two can coexist in one sentence with no conflict since they answer different questions (¿Caminaste por el centro para comprarlo?); sharpest minimal-pair contrast drilled: pasar por Barcelona (passing through, en route elsewhere) vs. ir para Barcelona (Barcelona itself is the destination) | spanish-lessons/day-51.html |
| 2026-09-01 | 52 | 關係代名詞(Los Pronombres Relativos: Que, Quien, Donde, Cuyo) | Steps outside the tense/mood/preposition tracks to cover Spanish's four core relative pronouns: que (universal default for people/things, never omissible unlike English that/who), quien/quienes (people only, most common right after a preposition or in a comma-set-off clause), donde (location, unaccented — distinct from the interrogative dónde), and cuyo/cuya/cuyos/cuyas (possession, agreeing in gender/number with the noun possessed rather than the possessor — the reverse of English/Chinese intuition, and the sharpest trap in the lesson) | spanish-lessons/day-52.html |

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
| 2026-07-29 | 20 | 觀 (Guān) — Contemplation |
| 2026-07-30 | 21 | 噬嗑 (Shì Kè) — Biting Through |
| 2026-07-31 | 22 | 賁 (Bì) — Grace |
| 2026-08-01 | 23 | 剝 (Bō) — Splitting Apart |
| 2026-08-02 | 24 | 復 (Fù) — Return |
| 2026-08-03 | 25 | 无妄 (Wú Wàng) — Innocence / The Unexpected |
| 2026-08-04 | 26 | 大畜 (Dà Chù) — The Taming Power of the Great |
| 2026-08-05 | 27 | 頤 (Yí) — Nourishment / The Corners of the Mouth |
| 2026-08-06 | 28 | 大過 (Dà Guò) — Preponderance of the Great / Great Exceeding |
| 2026-08-07 | 29 | 坎 (Kǎn) — The Abysmal / Water |
| 2026-08-08 | 30 | 離 (Lí) — The Clinging / Fire |
| 2026-08-09 | 31 | 咸 (Xián) — Influence / Wooing / Feeling |
| 2026-08-10 | 32 | 恆 (Héng) — Duration / Perseverance |
| 2026-08-11 | 33 | 遯 (Dùn) — Retreat |
| 2026-08-12 | 34 | 大壯 (Dà Zhuàng) — The Power of the Great |
| 2026-08-13 | 35 | 晉 (Jìn) — Progress |
| 2026-08-14 | 36 | 明夷 (Míng Yí) — Darkening of the Light |
| 2026-08-15 | 37 | 家人 (Jiā Rén) — The Family (The Clan) |
| 2026-08-17 | 38 | 睽 (Kuí) — Opposition |
| 2026-08-18 | 39 | 蹇 (Jiǎn) — Obstruction |
| 2026-08-19 | 40 | 解 (Xiè) — Deliverance |
| 2026-08-20 | 41 | 損 (Sǔn) — Decrease |
| 2026-08-21 | 42 | 益 (Yì) — Increase |
| 2026-08-22 | 43 | 夬 (Guài) — Breakthrough (Resoluteness) |
| 2026-08-23 | 44 | 姤 (Gòu) — Coming to Meet |
| 2026-08-24 | 45 | 萃 (Cuì) — Gathering Together |
| 2026-08-26 | 46 | 升 (Shēng) — Pushing Upward / Ascending |
| 2026-08-27 | 47 | 困 (Kùn) — Oppression / Exhaustion |
| 2026-08-28 | 48 | 井 (Jǐng) — The Well |
| 2026-08-29 | 49 | 革 (Gé) — Revolution (Molting) |
| 2026-08-30 | 50 | 鼎 (Dǐng) — The Caldron |
| 2026-08-31 | 51 | 震 (Zhèn) — The Arousing (Shock, Thunder) |
| 2026-09-01 | 52 | 艮 (Gèn) — Keeping Still (Mountain) |

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
| 2026-07-29 | Sri Lanka (斯里蘭卡) |
| 2026-07-30 | Bosnia and Herzegovina (波士尼亞與赫塞哥維納) |
| 2026-07-31 | Nigeria (奈及利亞) |
| 2026-08-01 | Vietnam (越南) |
| 2026-08-02 | Chile (智利) |
| 2026-08-03 | Kurdistan (庫德斯坦) |
| 2026-08-04 | Ethiopia (衣索比亞) |
| 2026-08-05 | Armenia (亞美尼亞) |
| 2026-08-06 | Bolivia (玻利維亞) |
| 2026-08-07 | Jordan (約旦) |
| 2026-08-08 | Papua New Guinea (巴布亞紐幾內亞) |
| 2026-08-09 | Timor-Leste (東帝汶) |
| 2026-08-10 | Madagascar (馬達加斯加) |
| 2026-08-11 | Kiribati (吉里巴斯) |
| 2026-08-12 | Lesotho (賴索托) |
| 2026-08-13 | Eswatini (史瓦帝尼) |
| 2026-08-14 | Liechtenstein (列支敦斯登) |
| 2026-08-15 | Qatar (卡達) |
| 2026-08-17 | Nauru (諾魯) |
| 2026-08-18 | Bangladesh (孟加拉) |
| 2026-08-19 | Kenya (肯亞) |
| 2026-08-20 | South Sudan (南蘇丹) |
| 2026-08-21 | Rwanda (盧安達) |
| 2026-08-22 | Djibouti (吉布地) |
| 2026-08-23 | Suriname (蘇利南) |
| 2026-08-24 | Georgia (喬治亞) |
| 2026-08-26 | Cuba (古巴) |
| 2026-08-27 | Malaysia (馬來西亞) |
| 2026-08-28 | North Korea (北韓) |
| 2026-08-29 | Chad (查德) |
| 2026-08-30 | Portugal (葡萄牙) |
| 2026-08-31 | Comoros (葛摩/科摩羅) |
| 2026-09-01 | Botswana (波札那) |

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
| 2026-07-29 | 母湯 (Mǔ Tāng, Taiwan) |
| 2026-07-30 | Hide the Pain Harold (忍痛哈羅德) |
| 2026-07-31 | Grumpy Cat (生氣貓) |
| 2026-08-01 | Nyan Cat (彩虹貓) |
| 2026-08-02 | Trollface (酸民臉) |
| 2026-08-03 | Success Kid (成功寶寶) |
| 2026-08-04 | Stonks |
| 2026-08-05 | "Karen" |
| 2026-08-06 | 傻眼貓咪 (Blank/Stunned Cat, Taiwan) |
| 2026-08-07 | 藍瘦香菇 (Lán Shòu Xiāng Gū, mainland China) |
| 2026-08-08 | Harambe |
| 2026-08-09 | Salt Bae |
| 2026-08-10 | "Kermit Sipping Tea" / "But That's None of My Business" |
| 2026-08-11 | Coffin Dance / Dancing Pallbearers ("Astronomia" meme) |
| 2026-08-12 | Bad Luck Brian |
| 2026-08-13 | Damn Daniel |
| 2026-08-14 | Surprised Pikachu (驚訝皮卡丘) |
| 2026-08-15 | Drakeposting / Drake Hotline Bling Meme |
| 2026-08-17 | LOLcats / "I Can Has Cheezburger?" |
| 2026-08-18 | Charlie Bit My Finger |
| 2026-08-19 | Left Shark |
| 2026-08-20 | All Your Base Are Belong to Us |
| 2026-08-21 | "Ain't Nobody Got Time for That" (Sweet Brown) |
| 2026-08-22 | Ugandan Knuckles ("Do You Know Da Wae?") |
| 2026-08-23 | "Is This a Pigeon?" |
| 2026-08-24 | Spider-Man Pointing at Spider-Man |
| 2026-08-26 | Dat Boi |
| 2026-08-27 | "87分,不能再高了" (87 Points, Can't Go Any Higher, Taiwan) |
| 2026-08-28 | Gigachad |
| 2026-08-29 | Tung Tung Tung Sahur |
| 2026-08-30 | Sigma / Sigma Male / Sigma Grindset |
| 2026-08-31 | Big Chungus |
| 2026-09-01 | Wojak |

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
| 2026-07-29 | Nosferatu (1922, dir. F.W. Murnau) |
| 2026-07-30 | The Godfather (1972, dir. Francis Ford Coppola) |
| 2026-07-31 | Flamenco (弗拉明戈) |
| 2026-08-01 | 2001: A Space Odyssey (1968, dir. Stanley Kubrick) |
| 2026-08-02 | Noh Theatre (能) |
| 2026-08-03 | Kathakali (卡達卡利, India) |
| 2026-08-04 | Butoh (舞踏, Japan) |
| 2026-08-05 | The Battle of Algiers (大戰阿爾及爾, 1966, dir. Gillo Pontecorvo) |
| 2026-08-06 | Swan Lake (天鵝湖, ballet, 1877/1895; music by Tchaikovsky, choreography by Petipa & Ivanov) |
| 2026-08-07 | Metropolis (大都會, 1927, dir. Fritz Lang) |
| 2026-08-08 | In the Mood for Love (花樣年華, 2000, dir. Wong Kar-wai) |
| 2026-08-09 | Commedia dell'arte (藝術喜劇, Italy) |
| 2026-08-10 | Wayang Kulit (皮影戲, Indonesia) |
| 2026-08-11 | Tokyo Story (東京物語, 1953, dir. Yasujiro Ozu) |
| 2026-08-12 | Rashomon (羅生門, 1950, dir. Akira Kurosawa) |
| 2026-08-13 | Waiting for Godot (等待果陀, 1953, by Samuel Beckett) |
| 2026-08-14 | Taiwanese Opera / Gezaixi (歌仔戲, Koa-á-hì, Taiwan) |
| 2026-08-15 | Kunqu Opera (崑曲, Kūnqǔ) |
| 2026-08-17 | Apocalypse Now (現代啟示錄, 1979, dir. Francis Ford Coppola) |
| 2026-08-18 | The Seventh Seal (第七封印, 1957, dir. Ingmar Bergman) |
| 2026-08-19 | Bharatanatyam (婆羅多舞, India) |
| 2026-08-20 | 8½ (Otto e mezzo, 1963, dir. Federico Fellini) |
| 2026-08-21 | Bicycle Thieves (Ladri di biciclette, 1948, dir. Vittorio De Sica) |
| 2026-08-22 | Argentine Tango (探戈) |
| 2026-08-23 | Do the Right Thing (為所應為, 1989, dir. Spike Lee) |
| 2026-08-24 | Vertigo (迷魂記, 1958, dir. Alfred Hitchcock) |
| 2026-08-26 | Sunset Boulevard (日落大道, 1950, dir. Billy Wilder) |
| 2026-08-27 | Casablanca (北非諜影, 1942, dir. Michael Curtiz) |
| 2026-08-28 | Cantonese Opera (粵劇) |
| 2026-08-29 | Singin' in the Rain (萬花嬉春, 1952, dir. Gene Kelly & Stanley Donen) |
| 2026-08-30 | The Rite of Spring (春之祭, ballet, 1913; music by Stravinsky, choreography by Nijinsky) |
| 2026-08-31 | Vietnamese Water Puppetry (Múa Rối Nước, 越南水上木偶戲) |
| 2026-09-01 | Persona (1966, dir. Ingmar Bergman) |

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
| 2026-07-29 | Narrative Structure (non-linear/achronological storytelling, framing devices, dramatic irony through resequencing) | Pulp Fiction (1994, dir. Quentin Tarantino) — the diner scene that opens and closes the film: because the timeline is scrambled, the internal-chronology-last diner robbery is shown first and last, letting Vincent Vega appear alive in the closing scene despite dying mid-film, and structurally placing Jules's redemptive choice above the story's "actual" chronological ending |
| 2026-07-30 | Blocking & Staging (vertical position and depth as power, physical distance as intimacy/threat, stillness vs. movement as center of gravity) | The Godfather (1972, dir. Francis Ford Coppola) — the opening office scene, where the camera slowly dollies back from a tight close-up on Bonasera to reveal Vito Corleone seated centrally and still behind his desk with his sons staged around him in a symmetrical wedge; Bonasera's escalating physical approach toward Vito's chair against Vito's near-total stillness stages the scene's entire power imbalance without a line of dialogue stating it |
| 2026-07-31 | Framing & Composition (symmetry vs. asymmetry, one-point perspective, negative space, breaks in established composition as narrative signals) | The Shining (1980, dir. Stanley Kubrick) — Danny's tricycle rides through the Overlook Hotel's corridors, tracked in perfectly centered one-point perspective toward a single vanishing point, with the rigid symmetry visually encoding the hotel's inhuman order until the shot's composition is escalated (not simply broken) into the uncanny, doll-like mirrored symmetry of the Grady twins appearing dead-center in the frame |
| 2026-08-01 | Symbolism & Visual Metaphor (a recurring visual object/gesture standing in for an unstated abstract idea — must recur, be diegetically grounded, and have its final appearance reframe everything prior) | 2001: A Space Odyssey (1968, dir. Stanley Kubrick) — the monolith, an identical black slab reused across three scenes spanning millions of years (prehistoric apes, buried on the Moon, at Bowman's deathbed), whose unchanging form transfers the dread/awe built in its first appearance instantly onto each later one, with its final appearance retroactively reframing the earlier two as stages of one evolutionary leap |
| 2026-08-02 | Auteur Theory / Director's Signature Analysis (reading a recurring visual/thematic fingerprint across a director's whole filmography, not a single scene — must be consistent across unrelated films, distinctive enough to identify blind, and tied to a worldview rather than a mere technical tic) | Wes Anderson's filmography, focused through The Grand Budapest Hotel (2014) — centered symmetrical framing, flat "dollhouse" blocking, 90-degree whip-pans, handcrafted miniature production design, nested chapter-book narration, and a deadpan ensemble delivery style recur identically across Bottle Rocket, Rushmore, The Royal Tenenbaums, and Moonrise Kingdom, proving the traits are an authorial signature rather than a single film's stylistic choice |
| 2026-08-03 | The Long Take / Plan-Séquence & Camera Choreography (an unbroken shot sustained across a scene, forcing the camera to do editing's job through reframing and blocking; look for how movement replaces cuts, how tightly choreography must be timed with no cut to hide errors, and the immersive/verisimilitude effect of never granting a cutaway) | Children of Men (2006, dir. Alfonso Cuarón, cinematography by Emmanuel Lubezki) — the car ambush sequence, a rig-mounted camera rotating a full 360 degrees inside/around the vehicle in unbroken real time as an attack unfolds, keeping the ambush's geography continuously legible and denying the audience any editorial relief the trapped characters don't get |
| 2026-08-04 | Performance / Acting Analysis (naturalism vs. stylization, internal vs. external technique, micro-behavior in wordless moments, vocal control and its breakdown, physical transformation, and how camera distance scales a performance) | There Will Be Blood (2007, dir. Paul Thomas Anderson) — the bowling-alley finale, where Daniel Day-Lewis's Daniel Plainview moves from controlled, mocking menace ("I drink your milkshake") to genuine unraveling rage, tracked through vocal disintegration and escalating physical aggression across extended, minimally-cut takes that force the performance itself to carry the scene |
| 2026-08-05 | Genre & Convention Analysis (reading a film against the accumulated iconography/tropes of its whole genre — does it satisfy, subvert, or hybridize genre expectations, and what ideology rides along with the convention itself) | Unforgiven (1992, dir. Clint Eastwood) — the final showdown at Skinny's saloon, which quotes every iconographic beat of the classical Western gunfight (aging gunslinger, walk into the saloon, drawn pistol) but stages it at night in rain and lamplight with a graceless, morally ugly kill rather than a cleansing catharsis, using the audience's genre literacy to indict the Western's traditional "righteous violence" mythology |
| 2026-08-06 | The Gaze / Spectatorship Theory (Laura Mulvey's "male gaze": whose eyes the camera borrows, whether the plot's engine is the act of looking itself, whether the audience's gaze is aligned with or exposed apart from a character's, and whose point-of-view is withheld) | Vertigo (1958, dir. Alfred Hitchcock) — the hotel-room transformation scene, an unbroken 360-degree pan around Scottie and Judy's kiss under green neon light, staged entirely around Scottie's obsessive look with no comparable POV given to Judy, dissolving mid-turn into the earlier scene of Madeleine's death to visually enact his desire to merge the woman in front of him with his memory |
| 2026-08-07 | Camera Movement (naming pan/tilt/dolly-tracking/crane/Steadicam/zoom precisely, then asking whether a movement is motivated or unmotivated, whether it reveals new space or is purely expressive, and whether it's meant to be invisible continuity-style or foregrounded as an authorial gesture — distinct from Day 3's light/colour-focused cinematography lesson and Day 8's static-frame composition lesson) | Goodfellas (1990, dir. Martin Scorsese) — the unbroken ~3-minute Steadicam tracking shot following Henry and Karen through the Copacabana's back kitchen entrance into the main showroom, where the physically motivated (they're really walking that route) yet purely expressive glide delivers the seductive "having pull" fantasy of mob life directly through unbroken movement before any dialogue states it |
| 2026-08-08 | Depth of Field & Focus (deep focus vs. shallow focus vs. rack focus; what is kept legible vs. deliberately obscured, whether a focus shift is a reveal or an emotional pivot, and whether the frame's depth of field matches how much control/clarity the scene grants its characters — distinct from Day 3's light/colour-focused cinematography lesson) | E.T. the Extra-Terrestrial (1982, dir. Steven Spielberg, cinematography by Allen Daviau) — the toolshed reveal, where a rack focus pulls sharpness away from heavily blurred foreground cornstalks onto E.T.'s previously illegible silhouette, delivering the reveal through focus alone (no cut, no camera movement) and keeping the audience locked into Elliott's exact gradual, childlike rate of discovery |
| 2026-08-09 | Continuity Editing & the 180-Degree Rule (Shot/Reverse Shot) (the imaginary axis of action, keeping screen direction consistent across cuts, eyeline matches, and whether the convention is followed invisibly or deliberately bent for unease — distinct from Day 2's broader editing-for-meaning/montage lesson) | The Silence of the Lambs (1991, dir. Jonathan Demme, cinematography by Tak Fujimoto) — the Hannibal Lecter interrogation scenes, where reverse shots align both actors' eyelines almost directly with the lens rather than the usual offset over-the-shoulder angle, keeping the 180-degree axis intact while making the convention itself the source of discomfort |
| 2026-08-10 | Aspect Ratio & Screen Format as a Storytelling Device (frame shape/width-to-height ratio as connotation before a shot is even composed; boxier ratios for intimacy/confinement vs. wider ratios for scale; the advanced case of a deliberate mid-film ratio change marking a shift in time period — distinct from Day 8's within-frame composition lesson) | The Grand Budapest Hotel (2014, dir. Wes Anderson, cinematography by Robert Yeoman) — three nested time layers each get their own aspect ratio (1.85:1 for the 1985/1968 frame story, 2.35:1 anamorphic for a 1960s middle layer, and boxy 1.37:1 Academy ratio for the 1932 core narrative), letting the frame's shape alone signal which time period the audience is in and reinforcing Anderson's centered symmetrical compositions |
| 2026-08-11 | Match Cut & Graphic Match (joining two shots via a shared graphic shape or motion vector across the cut, foregrounding the edit itself as a deliberate visual rhyme rather than hiding it — distinct from Day 2's Kuleshov/montage-juxtaposition lesson and Day 9's continuity-editing lesson) | Lawrence of Arabia (1962, dir. David Lean, cinematography by Freddie Young) — the match cut from Lawrence blowing out a lit match to a blazing desert sunrise, the shared flame-shape scaling instantly from matchstick to sun to convey his mythic transformation without a line of dialogue |
| 2026-08-12 | Costume Design & Wardrobe as Characterization/Worldbuilding (whether a costume evolves to index a character's internal change, whether costume is used as worldbuilding shorthand for an invented culture's social structure/technology/history, and whether a deliberate anachronism or exaggeration functions as authorial commentary — distinct from Day 3's cinematography/colour-grading lesson and Day 10's aspect-ratio lesson) | Black Panther (2018, dir. Ryan Coogler, costume design by Ruth Carter) — Wakanda's five tribes are costumed by fusing real African textile traditions (Basotho blanket patterns for the Border Tribe, Maasai beadwork, Tuareg garments, Dogon-inspired royal silhouettes) with vibranium-tech materials, communicating the fictional nation's political structure and Afrofuturist synthesis of tradition and technology through wardrobe alone |
| 2026-08-13 | Shot Scale / Size (close-up vs. wide/establishing shot as a distinct axis from focus, aspect ratio, or in-frame composition — contrast between scales builds tension through cutting rhythm alone, withholding or granting a close-up controls emotional distance, and an establishing shot's presence or deliberate absence controls spatial orientation) | The Good, the Bad and the Ugly (1966, dir. Sergio Leone, cinematography by Tonino Delli Colli) — the Sad Hill Cemetery three-way standoff, intercutting extreme close-ups of the gunslingers' eyes and holstered hands with wide establishing shots of the circular arena, escalating purely through shot-scale rhythm timed to Ennio Morricone's score |
| 2026-08-14 | Production Design & Art Direction (world-building through sets, architecture, and props — distinct from Day 12's costume lesson, Day 3's cinematography/colour lesson, and Day 1's broader mise-en-scène umbrella; look for verticality/scale as power hierarchy, cultural bricolage building an invented world from blended real-world reference points, and texture/decay as unspoken backstory) | Blade Runner (1982, dir. Ridley Scott, production design by Lawrence G. Paull, concept design by Syd Mead) — the opening flying-car descent into Los Angeles, contrasting the towering, Mayan-revival Tyrell Corporation pyramid bathed in isolated light against the street-level bricolage of mixed-script neon, steam vents, and rain-soaked crowds, establishing the film's entire class-stratified dystopia through vertical production-design contrast alone |
| 2026-08-15 | Adaptation Analysis (comparing a film to its literary/other source material via point-of-view translation, deliberate omissions/additions, and altered endings, rather than judging "fidelity" to plot events — a different lens from any prior lesson) | Jaws (1975, dir. Steven Spielberg), adapted from Peter Benchley's 1974 novel — Spielberg cut the novel's Ellen/Hooper affair and mafia-debt subplots to narrow the story into pure survival-horror; the malfunctioning mechanical shark forced a withhold-and-suggest visual strategy (POV shots, barrels, fin cutaways, Williams's two-note motif) now considered more effective than showing the creature; and the novel's anticlimactic drowning death was replaced with the film's explosive scuba-tank kill shot, trading "realism" for cinematic genre payoff |
| 2026-08-17 | Title Sequence as Thesis Statement (a main title sequence as a compressed short film establishing tone/genre/psychology before any story dialogue — check whether typography/material texture carries meaning, whether the imagery is diegetic or symbolic, how music relates to the images, and whether the sequence stands alone as a self-contained short — distinct from all 23 prior lessons, none of which addressed the title sequence itself as an object of analysis) | Se7en (1995, dir. David Fincher), title design by Kyle Cooper — extreme-close-up, hand-scratched Kodalith footage of the killer's hands assembling obsessive notebooks, intercut with a hooded silhouette and scored to a discordant industrial remix of Nine Inch Nails' "Closer," a sequence so unusually effective that test audiences reportedly applauded when it ended, credited with reviving Hollywood's interest in title design as a serious art form |
| 2026-08-18 | Cross-Cutting / Parallel Editing for Simultaneity (intercutting between two or more genuinely-simultaneous lines of action in different places — distinct from Day 2's Soviet-montage juxtaposition of unrelated shots and Day 6's achronological narrative restructuring; look for whether the alternating rhythm accelerates, whether the effect is ironic contrast or converging suspense, and whether continuous music/sound binds the separate locations into one event) | The Godfather (1972, dir. Francis Ford Coppola) — the baptism sequence, intercutting Michael Corleone's solemn Latin renunciation of Satan as godfather with the simultaneous, coordinated assassination of the Five Families' bosses, Nino Rota's unbroken church-organ score binding sacred ritual and profane violence into one event and delivering the scene's central irony through editing structure alone |
| 2026-08-19 | The Subjective / POV Camera (a shot placed at a character's own eyeline so the audience sees exactly what that character sees — distinct from Day 6's Gaze Theory, a structural/ideological lens about who is permitted to look, and Day 15's Camera Movement, which addresses physical travel rather than eyeline placement; look for framing/editing cues marking a shot as subjective, whose eyes they are, whether the POV is sustained unbroken or interrupted by objective cutaways, and what identity/motive the device withholds until it breaks) | Halloween (1978, dir. John Carpenter) — the four-minute unbroken Steadicam opening tracking shot from young Michael Myers's subjective POV, peering through a window, circling the house, retrieving a knife, and lifting a clown mask over the shot's own "eyes" moments before the murder, implicating the audience in the killer's perspective well before the final beat reveals a child beneath the mask |
| 2026-08-20 | Foreshadowing & Chekhov's Gun (a narrative/visual detail deliberately planted early — with just enough weight to register but not enough to telegraph its payoff — that returns to carry significance the audience could not have fully grasped on first appearance; distinct from Day 6's Narrative Structure, which addresses overall plot shape/sequencing, and Day 17's Title Sequence lesson, a compressed thesis delivered before the story begins; check whether the plant honors or deliberately violates the strict "every gun must fire" principle, whether it is visual or verbal, and how recognizing it on a rewatch reframes its first appearance) | Parasite (2019, dir. Bong Joon-ho) — the ornamental "scholar's rock" (수석, suseok) gifted to the Kim family early as a token of prosperity, carried instinctively by Ki-woo out of the rising sewage floodwater, and finally turned into an actual weapon in the violent climax, retroactively reframing the family's earlier aspirational hope in the object as always having carried the seed of harm |
| 2026-08-21 | Voice-Over Narration & Narrator Reliability (whose voice is narrating and from what vantage point in time; whether narration is redundant with, additive to, or actively contradicts the image track; distinct from Day 6's Narrative Structure, which addresses plot sequencing regardless of narration, and Day 4's Sound Design lesson, which covers score/diegetic sound broadly rather than a speaking narrator specifically; check whether the narrator is internal or external to the story, whether image and narration ever visibly conflict, and whether the film eventually reveals the narration itself to have been unreliable) | Fight Club (1999, dir. David Fincher) — the unnamed Narrator's confident, continuous voice-over throughout, revealed in the third act to be the account of a dissociative alter-ego (Tyler Durden) he has literally been narrating himself into and out of, retroactively exposing subliminal single-frame Tyler flashes planted throughout the "normal" early scenes that the narration never once mentioned |
| 2026-08-22 | Lens Choice & Focal Length: Wide-Angle vs. Telephoto Compression (how a lens's focal length alone shapes perceived spatial distance before any editing/lighting choice — wide-angle exaggerates foreground-background distance while telephoto flattens/compresses it; distinct from Day 8's Depth of Field & Focus (sharp vs. blurred, not spatial compression), Day 3's Cinematography & Lighting (light/color, not lens geometry), and Day 15's Camera Movement (physical camera travel, not a fixed lens's optical property); check what focal length is evidently in use, whether the resulting distortion is emotionally/narratively motivated, and whether a lens-choice shift mid-film marks a deliberate psychological or narrative turn) | The Graduate (1967, dir. Mike Nichols, cinematography by Robert Surtees) — the famous extreme-telephoto shot of Benjamin Braddock sprinting toward camera, whose severe compression flattens his forward progress so completely that despite a full sprint he appears to barely close any distance, conveying his exhausting, futile race against time through pure optics with no trick editing |
| 2026-08-23 | Sound Bridge (J-Cut & L-Cut) (audio deliberately overlapping a picture cut — arriving early as a J-cut or lingering late as an L-cut — to make a transition feel causally/emotionally continuous rather than abrupt; distinct from Day 4's broader Sound Design & Score, Day 2's Editing & Montage juxtaposition, and Day 11's purely visual Match Cut; check whether the overlapping sound is diegetic or non-diegetic, whether it's a J-cut building anticipation or an L-cut letting an emotional beat carry forward, and whether the bridge serves narrative economy or ironic contrast) | Apocalypse Now (1979, dir. Francis Ford Coppola) — the opening sequence, where helicopter-rotor sound begins over the burning jungle and continues unbroken as the picture cuts to Willard alone in his Saigon hotel room, fusing the war outside with the war in his head before the famous match cut to the ceiling fan whose blades visually echo the rotor sound that never stopped |
| 2026-08-24 | The Jump Cut (deliberately cutting between two too-similar shots of the same subject to produce a visible, jarring "jump" rather than smooth continuity; distinct from Day 9's Continuity Editing & 180-Degree Rule, which preserves spatial/temporal coherence, and Day 11's Match Cut, a visual rhyme between distinct shots rather than a discontinuity within one ongoing shot; check whether it serves narrative economy (skipping dead time) or psychological jolt, whether it occurs within a single ongoing shot or across a rhythmic staccato sequence, and whether the film treats it as an error to smooth over or a badge of stylistic rebellion) | Breathless (À bout de souffle, 1960, dir. Jean-Luc Godard) — the car scene where Michel drives Patricia through Paris; footage was cut out of the static conversation shot, leaving her position and the background visibly jumping between cuts despite being the same continuous moment, turning a budget-driven fix into a defining French New Wave assault on classical Hollywood continuity |
| 2026-08-26 | The Dutch Angle / Canted Framing (tilting the camera off its horizontal axis so the horizon runs diagonally, signaling imbalance/instability/moral distortion before dialogue or action states it; distinct from Day 8's Framing & Composition, which covers symmetry/perspective/negative space within a level frame, and Day 3's Cinematography & Lighting, which covers light/color rather than the camera's rotational axis; check whether the tilt is a single punctuation moment or a sustained stylistic signature, whether it's subtle or extreme, and whether it's motivated by a character's literal disorientation or is purely authorial commentary) | The Third Man (1949, dir. Carol Reed, cinematography by Robert Krasker) — set across occupied postwar Vienna, the film repeatedly cants the frame (interrogation scenes, the climactic sewer chase) as pure authorial commentary that the world's moral/physical foundations are off-level, considered daringly excessive by some contemporaries yet now a textbook reference case for the technique |
| 2026-08-27 | Breaking the Fourth Wall / Direct Address to Camera (a character or the film itself acknowledges it is being watched, collapsing the fiction of a sealed world unaware of an audience; distinct from Day 21's Voice-Over Narration, where a narrator's voice runs over the images without ever looking at or acknowledging the camera/audience, and Day 19's Subjective/POV Camera, which places the lens at a character's eyeline without that character being aware of a camera at all; check whether the break is a single punctuation moment or a sustained structural device, whether the character is genuinely aware they address an audience, and what relationship it builds — conspiratorial intimacy, comic mockery, or unsettling implication) | Ferris Bueller's Day Off (1986, dir. John Hughes) — Ferris turns to the camera within the film's opening minutes and keeps returning to it throughout, narrating his truancy scheme and personal philosophy and even breaking in after the credits start to roll to tell the audience to go home; by making the viewer his sole confidant and co-conspirator, the device recruits the audience into rooting for a protagonist who is objectively lying to and manipulating almost everyone else in his life |
| 2026-08-28 | The Dolly Zoom / "Vertigo Effect" (Contra-Zoom) (physically dollying the camera toward or away from a subject while simultaneously zooming the lens in the opposite direction, holding the subject's frame size constant while the background stretches or compresses around it — an effect neither a plain zoom nor a plain dolly can produce alone; distinct from Day 15's Camera Movement, which named "zoom" as one movement among several in a broad taxonomy without addressing this specific simultaneous zoom-against-dolly combination or its disorienting perceptual effect; check what psychological state it externalizes, whether the background stretches away or compresses toward the viewer, and whether it's a single shock beat or a recurring structural motif) | Jaws (1975, dir. Steven Spielberg, cinematography by Bill Butler) — the beach scene where police chief Martin Brody realizes in real time that a shark is attacking a swimmer; Spielberg dollies the camera toward Brody while zooming the lens out, holding his face at a constant size while the beach behind him appears to lurch and stretch away, externalizing the sensation of the ground dropping out from under his sense of control without a single line of dialogue; deliberately borrowed from Vertigo (1958, dir. Alfred Hitchcock), whose use of the technique for Scottie's fear of heights gave the effect its popular name |
| 2026-08-29 | Ellipsis / Editing for Compressed Time (a cut, dissolve, or montage that deliberately skips a stretch of story time without confusing the audience about how much has passed — distinct from Day 24's Jump Cut, which cuts between two too-similar shots within one continuous moment to produce a jarring visible discontinuity, and Day 18's Cross-Cutting/Parallel Editing, which alternates between genuinely simultaneous actions in different places rather than compressing time within one ongoing action; ellipsis smooths the gap over rather than exposing it, typically signaled by a dissolve, a recurring visual/musical motif, or a costume/prop change; check how much time is skipped, what cue marks the jump, whether the missing time is genuinely irrelevant or withheld for a later reveal, and whether it compresses years into a life-spanning montage or just hours/days into a simple dissolve) | Up (2009, dir. Pete Docter, co-dir. Bob Peterson) — the wordless "Married Life" opening montage, compressing roughly forty-five years of Carl and Ellie's entire marriage into about four minutes via rapid dissolves, recurring match-cut transitions, and a single Michael Giacchino musical theme binding every time-leap into one continuous emotional throughline, so Ellie's death moments later lands with the weight of an entire unseen lifetime |
| 2026-08-30 | Leitmotif / Recurring Musical Theme as Character Signature (a specific, identifiable musical phrase — not score in general — permanently attached to one character/place/idea, so hearing it (even varied in key, tempo, or orchestration) cues that character's presence independent of the image track; distinct from Day 4's broader Sound Design & Score, which covered score-as-emotional-cue and diegetic/non-diegetic sound generally without tracking one specific recurring theme's variations across a whole film/franchise; check what melodic/rhythmic cell repeats, whose identity it represents, whether its harmonic/instrumental treatment shifts to track that character's arc, and whether the film withholds or delays it for a later payoff) | Star Wars: The Empire Strikes Back (1980, dir. Irvin Kershner, music by John Williams) — "The Imperial March" (Darth Vader's Theme), introduced in this film (not the 1977 original) as Vader's musical signature, a grinding minor-key march related to the funeral-march tradition that announces his offscreen approach through sound alone, contrasted against the heroic major-key "Force Theme" to carry the trilogy's moral architecture in music even without dialogue |
| 2026-08-31 | Slow Motion & Speed Ramping / Frame-Rate Manipulation (overcranking records more frames per second than playback rate, stretching action into slow motion when played back normally; undercranking does the reverse; speed ramping shifts frame rate within one continuous shot rather than cutting between separately-shot segments; distinct from Day 24's Ellipsis, which skips time via editing/cuts rather than dilating it via frame rate, Day 3's Long Take, an unbroken shot at normal real-time speed regardless of frame rate, and Day 15's Camera Movement, physical camera travel independent of playback speed; check what psychological/dramatic beat is isolated and elongated, whether the effect is subtle or an overt stylistic signature, and whether sound is deliberately left unslowed for tension against the stretched image) | The Matrix (1999, dir. Lana & Lilly Wachowski, cinematography by Bill Pope) — the lobby shootout's "bullet time" sequence (VFX supervisor John Gaeta), combining a timed ring of still cameras with separately-shot slow-motion footage so the camera appears to orbit a subject frozen in extreme slow motion, isolating a fraction-of-a-second event to externalize Neo's dawning superhuman perception within the Matrix; built on the older slow-motion-violence tradition pioneered by Sam Peckinpah's The Wild Bunch (1969) |
| 2026-09-01 | The Freeze Frame (Arrested Motion) (halting the moving image on a single still frame for a deliberate duration rather than continuing to play, most often as a final punctuation device but occasionally mid-sequence to isolate one instant; distinct from Day 3's Long Take, an unbroken shot that keeps playing in real time — the opposite gesture of arresting motion — Day 15's Camera Movement, physical camera travel irrelevant once the image has stopped moving, and Day 37's Slow Motion & Speed Ramping, which stretches motion via frame rate but never fully halts it; check whether the freeze closes the film on a deliberately unresolved note or emphasizes a mid-scene instant, and whether it is total or partial) | The 400 Blows (Les Quatre Cents Coups, 1959, dir. François Truffaut) — the celebrated final shot, young runaway Antoine Doinel sprinting along a beach toward the sea in one continuous tracking shot, turning to look directly into the camera as the image abruptly freezes on his face in an extended close-up that becomes the film's last image before the credits, deliberately refusing to resolve his fate and becoming one of the most influential single shots of the French New Wave |

## Run Notes

**Archive notice (2026-08-20):** This file's Run Notes section was growing
large enough (~150KB) to repeatedly hit output-size limits when pushing
updates, corrupting the file mid-transmission. To fix this, the full
run-note history from 2026-07-14 through 2026-08-18 has been moved,
verbatim and unabridged, into three archive files:
- `ROUTINE_LOG_ARCHIVE_1.md` — 2026-07-14 through 2026-07-31
- `ROUTINE_LOG_ARCHIVE_2.md` — 2026-08-01 through 2026-08-08
- `ROUTINE_LOG_ARCHIVE_3.md` — 2026-08-10 through 2026-08-18
- `ROUTINE_LOG_ARCHIVE_4.md` — 2026-08-19 through 2026-08-27 (archived
  2026-08-29, once this file's Run Notes again grew past ~10 entries/45-50KB)

This file (`ROUTINE_LOG.md`) now keeps the Output Preferences, templates,
Main Briefing Sections list, all six never-repeat tracking tables (still
the authoritative source for what has already been used — always check
these, not the archives, before picking today's content), and only the
most recent run notes below. Future runs: after adding today's entry, if
this file's Run Notes section grows past roughly 8-10 daily entries
(~45-50KB), move the oldest entries out into a new
`ROUTINE_LOG_ARCHIVE_N.md` file (next sequential number) to keep this file
safely small, and update this notice accordingly.

- **2026-08-28 — clean run, STEP 0 applied correctly from the start.**
  Read the session's own `currentDate` context first (2026-08-27 UTC,
  which is already 2026-08-28 05:39 Taipei time — confirmed with `date`
  and `TZ=Asia/Taipei date`), rather than inferring "today" from the
  portal branch's latest entry. Computed `days_owed = 1` against the
  portal branch's latest entry (2026-08-27), so today's content was
  genuinely owed. Listed all `claude/*` branches via `list_branches` and
  cross-checked the GitHub Pages `deployments?environment=github-pages`
  endpoint: the most recent `state: success` deployment (id 6114520157,
  2026-08-27T00:50:28Z) confirmed the portal branch is still
  `claude/epic-brahmagupta-g1y16m`, currently at commit `8e087f0f...`
  (same commit as `claude/daily-2026-08-27-prompt-rules`). No branch in
  the full branch listing had a daily-dated entry past 2026-08-27, so the
  portal branch already held the longest, most complete, non-duplicate
  history — no reconciliation was needed this run. Created
  `claude/daily-2026-08-28` off the portal tip (confirmed via local
  `git fetch` + `git log` matching the same commit hash), wrote
  `briefings/2026-08-28.html` and `spanish-lessons/day-48.html`, and
  added Spanish Day 48 (el se impersonal y la voz pasiva refleja —
  impersonal/passive "se," the third and final identity of the se
  pronoun cluster, deliberately sequenced as the natural completion of
  Day 46's reflexive se and Day 47's reciprocal se), Hexagram 48 (井
  Jǐng, The Well — the Xugua commentary's direct pivot off Hexagram 47,
  "困乎上者必反下", read as a return to the most basic, inexhaustible
  resource after exhaustion at the heights; classical text cross-verified
  via WebSearch against multiple independent Chinese classical-text
  transcription sites since ctext.org itself was unreachable by direct
  fetch in this environment), North Korea (chosen for Section 5 as a
  populous, geopolitically significant East Asian state not yet covered;
  facts on population/GDP verified via WebSearch and flagged as soft
  outside estimates rather than official DPRK data), Gigachad (chosen for
  Section 6 as a still-highly-active, previously-uncovered meme; verified
  via WebSearch that the widely-repeated "Beyond the Gains" origin story
  and "Bashkir" ethnicity detail are NOT corroborated by any source found
  and were deliberately omitted from the briefing rather than stated
  unverified), and Cantonese Opera (chosen for Section 7 as a Chinese
  opera tradition clearly distinct from the already-covered Peking Opera,
  Kunqu, and Taiwanese Opera/Gezaixi; UNESCO inscription year and key
  performers verified via WebSearch). Section 8 added The Dolly Zoom /
  "Vertigo Effect" as the thirty-fourth film-analysis lesson, worked
  through Jaws' beach scene (cinematographer Bill Butler credit verified
  via WebSearch), chosen as a lens distinct from Day 15's general Camera
  Movement taxonomy since it isolates the specific simultaneous
  zoom-against-dolly combination rather than camera movement broadly.
  Market data for Section 1 required substantial WebSearch/WebFetch
  cross-checking: direct WebFetch to finance.yahoo.com, fool.com, and
  tradingeconomics.com were all blocked by the network egress proxy, so
  figures were reconstructed from WebSearch result summaries instead;
  an initial search returned an internally-inconsistent set of index
  levels (S&P 500 7,673.04/Dow 53,195.36/Nasdaq 26,168.46, all *below*
  the already-published Aug 27 briefing's Aug 26 closing figures despite
  being labeled as the Aug 27 close) which was caught precisely because
  of that inconsistency and discarded in favor of re-querying with
  session-specific context (Nvidia's earnings beat, Salesforce's rally,
  named Dow constituent movers) until a coherent, mutually-consistent
  picture emerged across independent sources (Dow +100pts/+0.19% to
  53,564 per a Trading-Economics-sourced summary naming specific movers;
  S&P 500 +0.57% to ~7,720 and Nasdaq +1.4-1.5% per Yahoo/Motley
  Fool/CNBC-sourced summaries) — flagged in the briefing's own meta note
  that the Nasdaq/S&P point levels are reconstructed/approximate rather
  than a single authoritative print. Asia/Taiwan figures (Nikkei -0.2%,
  KOSPI +1.5%, Hang Seng -0.3%, TAIEX +0.31% to 45,975 with TSMC itself
  dipping slightly) came from single, internally-detailed articles
  (tradingkey.com, nextapple.com) rather than aggregated summaries, so
  were treated as more reliable. Updated `index.html` and all six
  never-repeat tracking tables in this file. Fast-forward merged
  `claude/daily-2026-08-28` into `claude/epic-brahmagupta-g1y16m` and
  pushed the portal branch, making today's entry live at
  https://lebonthe.github.io/ClaudeRoutineTest/. The daily branch was
  kept (not deleted), per the no-destructive-action default.

- **2026-08-29 — clean run, STEP 0 and the branch-recovery procedure both
  applied before any content was written.** Read the actual current
  date/time directly via `TZ=Asia/Taipei date` (Sat 2026-08-29 05:38
  Taipei time) rather than inferring "today" from the portal branch's
  latest dated entry or any branch name. `mcp__github__list_branches`
  listed all `claude/*` branches in the repo (60 total). Per the standing
  instruction never to rely on the repo's unrelated `default_branch`
  setting, the GitHub Pages deployment source was confirmed via
  `mcp__github__actions_list` (`list_workflow_runs` on the
  `pages-build-deployment` workflow, since a direct
  `GET /repos/.../deployments?environment=github-pages` call via
  `WebFetch` again returned `403`, as on several prior runs): the most
  recent successful run (#49, 2026-08-27T21:56:37Z, i.e. 2026-08-28
  05:56 Taipei time) had `head_branch: claude/epic-brahmagupta-g1y16m`,
  confirming it as the persistent portal branch. That branch's
  `ROUTINE_LOG.md` (all six tracking tables) and `index.html` were
  fetched and confirmed complete and already fully up to date through
  Day 48/Hexagram 48/North Korea/Gigachad/Cantonese Opera/Dolly Zoom
  (2026-08-28) — no gap and nothing to reconcile from any other branch.
  `days_owed = 2026-08-29 minus 2026-08-28 = 1`, so today's content was
  produced (not skipped as a duplicate) and dated 2026-08-29. `git fetch
  origin claude/epic-brahmagupta-g1y16m` followed by `git checkout -b
  claude/daily-2026-08-29 origin/claude/epic-brahmagupta-g1y16m`
  confirmed the same tip locally before any file was written. Today's
  content: Spanish Day 49 (the classic ser-passive, contrasted directly
  with Day 48's se-passive — the natural next step after finishing se's
  three identities), Hexagram 49 (革 Gé, Revolution/Molting, continuing
  the King Wen sequence directly from yesterday's 井 Jǐng via the Xugua
  commentary's own explicit link between the two), Chad (a substantially
  larger, more populous country picked deliberately for variety after a
  recent run of very small states/micro-nations), "Tung Tung Tung Sahur"
  (a 2025 Indonesian AI-generated "brainrot" meme, chosen to represent
  the newest wave of Asian web culture rather than repeating an
  older/Western meme), Singin' in the Rain (1952) as the Section 7
  spotlight (the first movie-musical landmark covered in this series),
  and Ellipsis/Editing for Compressed Time as the 35th film-analysis
  method (Up's "Married Life" montage), distinguished explicitly from
  the already-taught Jump Cut and Cross-Cutting/Parallel Editing lessons
  to avoid conceptual overlap. Market section (Section 1) used Friday,
  2026-08-28 closes for all three regions (US, Asia, Taiwan) since
  Saturday 2026-08-29 is a weekend with no new session in any of them;
  figures were cross-checked across multiple independent search results
  (CNBC/Yahoo Finance for US; Trading Economics/247wallst/ts2.tech/
  Sunday Guardian for Nikkei/Hang Seng/Shanghai; Trading Economics for
  TAIEX) rather than taken from a single source, and the briefing's own
  meta note states explicitly that no market covered has a newer session
  to report. This file's Run Notes section had again grown past the
  ~10-entry/45-50KB threshold noted in the Archive notice above (10
  entries, ~120KB before today), so the nine oldest entries
  (2026-08-19 through 2026-08-27) were moved out verbatim into a new
  `ROUTINE_LOG_ARCHIVE_4.md`, leaving only the 2026-08-28 entry and this
  one in this file; the Archive notice above was updated accordingly.
  Updated `index.html` and all six never-repeat tracking tables in this
  file. Fast-forward merged `claude/daily-2026-08-29` into
  `claude/epic-brahmagupta-g1y16m` and pushed the portal branch, making
  today's entry live at https://lebonthe.github.io/ClaudeRoutineTest/.
  The daily branch was kept (not deleted), per the no-destructive-action
  default.


- **2026-08-30 — STEP 0 caught a stale `currentDate` context value before
  any work began.** The session's own `currentDate` context field read
  2026-08-29 — i.e. *yesterday's* date, already fully covered by the
  portal branch's latest entry — which is exactly the trap STEP 0 exists
  to catch. Rather than trusting that field at face value, `date -u` and
  `TZ=Asia/Taipei date` were run directly: the system clock showed Sat
  2026-08-29 21:39 UTC, i.e. **Sun 2026-08-30 05:39 Taipei time**, one full
  day ahead of the context field. Cross-checked against the portal
  branch's own history: the latest successful `pages-build-deployment`
  workflow run (#50, created_at 2026-08-28T21:52:13Z = 2026-08-29 05:52
  Taipei) had `head_branch: claude/epic-brahmagupta-g1y16m` at commit
  `75eecbac...`, matching `claude/daily-2026-08-29`'s tip exactly and
  confirming the portal branch's latest dated entry is 2026-08-29 — so
  `days_owed = 2026-08-30 minus 2026-08-29 = 1`, meaning today's content
  was genuinely owed and dated 2026-08-30 (not skipped as a duplicate,
  and not mistakenly dated 2026-08-29 a second time). `list_branches`
  returned 62 `claude/*` branches; none had a daily-dated entry past
  2026-08-29, so no reconciliation from another branch was needed. `git
  fetch origin claude/epic-brahmagupta-g1y16m` followed by `git checkout
  -b claude/daily-2026-08-30 origin/claude/epic-brahmagupta-g1y16m`
  confirmed the same tip locally before any file was written. Today's
  content: Spanish Day 50 (estar + past participle for resultant state,
  the direct pair to Day 49's ser-passive — same participle-agreement
  rule, opposite function: state vs. event, and estar can never take a
  "por + agente" phrase), Hexagram 50 (鼎 Dǐng, The Caldron, continuing
  the King Wen sequence directly from yesterday's 革 Gé via the Xugua
  commentary's explicit "革物者莫若鼎,故受之以鼎"), Portugal (chosen for
  Section 5 as a mid-sized, well-documented European state not yet
  covered, including its rare current "cohabitation" between a
  centre-left president elected March 2026 and a centre-right prime
  minister), "Sigma"/"Sigma Male"/"Sigma Grindset" (chosen for Section 6
  as a still highly-active, previously-uncovered meme with a well
  documented origin distinct from the already-covered Gigachad), The
  Rite of Spring (1913 ballet, chosen for Section 7 as the first dance/
  concert-music landmark covered that centers on a real historical riot
  at its premiere, distinct from the already-covered Swan Lake ballet),
  and Leitmotif/Recurring Musical Theme as the 36th film-analysis method
  (Star Wars: The Empire Strikes Back's Imperial March), distinguished
  explicitly from the already-taught Day 4 Sound Design & Score lesson
  to avoid conceptual overlap. Market section (Section 1) reused Friday,
  2026-08-28's closing figures verbatim from yesterday's briefing, since
  Saturday 2026-08-29 and Sunday 2026-08-30 are both non-trading days in
  all three regions covered (US/Asia/Taiwan) — the briefing's own meta
  note states explicitly that these are the same confirmed prints as
  yesterday's report, not an independently re-verified new session, to
  avoid presenting a repeated number as if it were freshly confirmed.
  Section 2 (dev news) was refreshed with genuinely new items not in
  yesterday's briefing: Apple CEO John Ternus's September 1, 2026
  succession from Tim Cook (making the Sept 9 event his first as CEO),
  a 100+-company (OpenAI/Anthropic/Google/Microsoft) joint letter on
  AI-enabled cyberattack defense, a since-patched cross-model
  reasoning-token API flaw, and new Flutter items (Widget Previewer IDE
  integration, #2 app-store SDK ranking, 2026 Toyota RAV4 infotainment).
  Updated `index.html` (new top row plus a Run Notes-referencing note
  about the stale-`currentDate` catch) and all six never-repeat tracking
  tables in this file. Fast-forward merged `claude/daily-2026-08-30` into
  `claude/epic-brahmagupta-g1y16m` and pushed the portal branch, making
  today's entry live at https://lebonthe.github.io/ClaudeRoutineTest/.
  The daily branch was kept (not deleted), per the no-destructive-action
  default.


- **2026-08-31 — clean run, STEP 0 applied correctly from the start.**
  Read the system clock directly (`date -u` → 2026-08-30T21:39Z;
  `TZ=Asia/Taipei date` → Mon 2026-08-31 05:39 CST) rather than trusting
  the session's own `currentDate` context field, which was itself
  reading 2026-08-30 — a day behind, the same category of staleness
  flagged on 2026-08-30's run. Computed `days_owed = 1` against the
  portal branch's latest entry (2026-08-30), so today's content was
  genuinely owed and dated 2026-08-31 (a Monday), not skipped as a
  duplicate. Listed all `claude/*` branches via `list_branches` (61
  branches returned) and confirmed the persistent portal branch via the
  `pages-build-deployment` GitHub Actions workflow's run history (the
  `deployments?environment=github-pages` REST endpoint was not directly
  callable through the available MCP tools this run, so the equivalent
  Actions-workflow-history method already validated in prior runs was
  used instead): the latest successful run (id 33277117353) deployed
  `claude/epic-brahmagupta-g1y16m` at commit `fac8d1899...`, which
  exactly matches `claude/daily-2026-08-30`'s tip — confirming the
  portal branch already held the complete, non-stale history through
  Day 50/Hexagram 50 with no reconciliation needed. Created
  `claude/daily-2026-08-31` directly off the portal branch's tip via
  local `git fetch origin claude/epic-brahmagupta-g1y16m` + `git
  checkout -b ... origin/...`, confirmed by matching commit hash. Wrote
  `briefings/2026-08-31.html` and `spanish-lessons/day-51.html`, adding
  Spanish Day 51 (Por vs. Para — deliberately stepping outside the
  tense/mood track to resolve Spanish learners' single most notorious
  point of confusion, contrasting por's backward-pointing cause/
  duration/route/exchange logic against para's forward-pointing
  purpose/recipient/deadline/destination logic, with the "pasar por
  Barcelona" vs. "ir para Barcelona" minimal pair as the sharpest
  worked contrast), Hexagram 51 (震 Zhèn, The Arousing/Shock/Thunder —
  the Xugua commentary's direct pivot off Hexagram 50, "主器者莫若長子,
  故受之以震", read as succession/continuity following the Caldron's
  consolidated order; classical text cross-verified against training
  knowledge of the standard Wilhelm/Baynes-style rendering, consistent
  with the pattern of prior hexagram entries in this table), Comoros
  (chosen for Section 5 as a small, previously-uncovered Indian Ocean
  archipelago nation and explicit "faction"-adjacent case given its
  20+ coups and the ongoing Mayotte sovereignty dispute; population,
  GDP-per-capita, and land-area figures verified fresh via WebSearch
  against Worldometer's 2026 figures, and current President Azali
  Assoumani's tenure cross-checked via WebSearch rather than relied on
  from training data alone, given the training cutoff predates this
  session's 2026 date), Big Chungus (chosen for Section 6 as a
  previously-uncovered, well-documented 2018 meme with a clear,
  verifiable origin story), and Vietnamese Water Puppetry / Múa Rối
  Nước (chosen for Section 7 as a distinct Southeast Asian traditional
  performing-art form not overlapping any of the Japanese/Chinese/
  Indian/Indonesian traditions already covered). Section 8 added Slow
  Motion & Speed Ramping / Frame-Rate Manipulation as the thirty-seventh
  film-analysis lesson, worked through The Matrix's (1999) "bullet
  time" lobby sequence, explicitly distinguished from Day 24's Ellipsis
  (edits skip time; this dilates it via frame rate), Day 3's Long Take
  (real-time duration regardless of frame rate), and Day 15's Camera
  Movement (physical travel independent of playback speed), and traced
  back to Sam Peckinpah's The Wild Bunch (1969) as the technique's
  slow-motion-violence precursor. Market section (Section 1) required
  cross-checking three independent WebSearch queries for the Hang Seng
  Index's Friday 2026-08-28 close after two initial results disagreed
  (+0.30% to 25,648.40 vs. +0.07% to 25,584.79 vs. a third result
  mislabeling the session as "Thursday" while reporting -0.3% to
  25,566) — the "Thursday" label was independently proven wrong by
  computing the weekday of 2026-08-28 from the already-confirmed
  2026-08-30-is-a-Sunday anchor (Aug 28 = Friday), so that figure was
  discarded per this file's stale/mislabeled-result guidance, and the
  remaining two-source-consistent figure (25,584.79, +0.07%) was used;
  US and Taiwan figures (incl. TSMC's NT$2,420 close and the Nvidia-
  earnings rally rationale) were corroborated across CNBC/Yahoo Finance
  and ETtoday/NextApple respectively with no discrepancy. Section 2
  (dev news) drew on genuinely current items: OpenAI's Astra model
  release slowdown over cybersecurity capabilities, the new GPT-5.6-
  Cyber model and two-tier Daybreak program, Microsoft's MAI-Cyber-1-
  Flash benchmark claims, Apple's third security patch round in three
  weeks (~30 vulnerabilities), and Flutter 3.47.0's stable release plus
  Agentic Hot Reload. Updated `index.html` (new top row) and all six
  never-repeat tracking tables in this file. Fast-forward merged
  `claude/daily-2026-08-31` into `claude/epic-brahmagupta-g1y16m` and
  pushed the portal branch, making today's entry live at
  https://lebonthe.github.io/ClaudeRoutineTest/. The daily branch was
  kept (not deleted), per the no-destructive-action default.

- **2026-09-01 — clean run, STEP 0 applied correctly from the start.**
  Read the system clock directly (`date -u` → Mon 2026-08-31T21:39:17Z;
  `TZ=Asia/Taipei date` → Tue 2026-09-01 05:39 CST) rather than inferring
  "today" from the portal branch's most recent entry or the session's
  own `currentDate` context field (which read 2026-08-31, a day behind —
  the same category of staleness flagged on 2026-08-30's run — so the
  system-clock check again proved essential). Computed `days_owed = 1`
  against the portal branch's latest entry (2026-08-31), so today's
  content was genuinely owed and dated 2026-09-01 (a Tuesday), not
  skipped as a duplicate. Listed all `claude/*` branches via
  `list_branches` (63 branches returned) and confirmed the persistent
  portal branch via the `deployments?environment=github-pages` REST API
  (called directly via `curl`, which worked this run): the latest
  `state: success` deployment (id 6171701056, 2026-08-30T21:54:03Z)
  deployed `claude/epic-brahmagupta-g1y16m` at commit `bacedd3f81...`,
  which exactly matches `claude/daily-2026-08-31`'s tip — confirming the
  portal branch already held the complete, non-stale history through
  Day 51/Hexagram 51 with no reconciliation needed. Created
  `claude/daily-2026-09-01` directly off the portal branch's tip via
  `create_branch`, confirmed by matching commit hash. Wrote
  `briefings/2026-09-01.html` and `spanish-lessons/day-52.html`, adding
  Spanish Day 52 (relative pronouns que/quien/donde/cuyo — deliberately
  stepping outside the tense/mood/preposition track to cover a
  foundational grammar gap, with cuyo's possessed-noun rather than
  possessor agreement flagged as the sharpest trap), Hexagram 52 (艮 Gèn,
  Keeping Still/Mountain — the Xugua commentary's direct pivot off
  Hexagram 51, "震者動也,物不可以終動,止之,故受之以艮", read as the
  disciplined-stillness counterpart to Hexagram 51's composure-under-
  shock lesson; classical text cross-verified against training
  knowledge of the standard Wilhelm/Baynes-style rendering, consistent
  with the pattern of prior hexagram entries in this table), Botswana
  (chosen for Section 5 as a previously-uncovered Southern African
  democracy with a strong post-independence diamond-driven economy and
  a notable 2024 peaceful transfer of power ending 58 years of
  single-party rule; population, area, and GDP-per-capita figures held
  from training knowledge given the low-volatility nature of these
  statistics, with the 2024 election outcome cross-checked against
  training knowledge of the Duma Boko/Umbrella for Democratic Change
  transition), Wojak (chosen for Section 6 as a previously-uncovered,
  foundational imageboard-culture template distinct from Pepe/Trollface/
  other already-covered entries, with its NPC/Doomer/Soyjak derivative
  taxonomy giving clear material for the "variations/evolution" and
  "current status" sub-points), and Persona (chosen for Section 7 as a
  landmark Bergman arthouse film not yet covered, pairing naturally with
  the already-featured 8½ as a defining work of 1960s reflexive
  psychological cinema). Section 8 added The Freeze Frame (Arrested
  Motion) as the thirty-eighth film-analysis lesson, worked through The
  400 Blows' (1959) closing freeze-frame shot, explicitly distinguished
  from Day 3's Long Take (real-time playback, the opposite gesture),
  Day 15's Camera Movement (physical travel, irrelevant once the image
  has stopped), and Day 37's Slow Motion & Speed Ramping (stretches
  motion via frame rate but never fully halts it). Market section
  (Section 1) required cross-checking multiple independent WebSearch
  queries for two discrepancies: an initial TAIEX search result
  mislabeled Monday 2026-08-31's 202.98-point decline as a "gain" (a
  garbled/stale figure), corrected via a re-query naming specific
  stocks (Nan Ya Plastics, Cathay Financial, Unimicron) and the MSCI
  quarterly rebalance, which returned multiple internally-consistent
  Chinese-language sources (Newtalk, Focus Taiwan) confirming the
  202.98-point decline to 46,128.47; and the Hang Seng Index showed
  -0.22% in one 24/7 Wall St snapshot versus -0.07% in another (and in
  a separate WebSearch synthesis), resolved by cross-checking three
  independent Chinese/Japanese-language sources (cnyes, Baidu, i-Cable)
  that all confirmed the smaller -0.07%/-17.8-point decline to
  25,566.99, with the -0.22% figure judged a stale intraday snapshot
  rather than the final close. US figures (S&P/Dow/Nasdaq, the US-Iran
  conflict/oil-price rationale) and the Nikkei/Shanghai figures were
  each corroborated across 2+ independent sources with no discrepancy.
  Weekday of 2026-08-31 independently confirmed as Monday via direct
  Python date computation, not assumed. Section 2 (dev news) drew on
  genuinely current items dated to this exact date where possible: Tim
  Cook's formal CEO-to-executive-chairman transition and John Ternus's
  succession landing precisely on 2026-09-01 itself, the confirmed
  Sept 9 "Surprise and Shine" event and iPhone 18 Pro/Pro Max/Ultra
  lineup-split rumors, the iOS 27 Siri overhaul, and Anthropic's
  confirmed Claude Sonnet 5 pricing decision and Claudeforce/Salesforce
  beta timeline (deliberately different specifics from 2026-08-31's
  briefing, which had already covered the security-patch-round and
  Astra/GPT-5.6-Cyber/MAI-Cyber-1-Flash items, to avoid redundant
  content between consecutive days). Updated `index.html` (new top row)
  and all six never-repeat tracking tables in this file. Pushed
  `briefings/2026-09-01.html` and `spanish-lessons/day-52.html` to
  `claude/daily-2026-09-01` via `push_files`, then will fast-forward
  merge `claude/daily-2026-09-01` into `claude/epic-brahmagupta-g1y16m`
  and push the portal branch, making today's entry live at
  https://lebonthe.github.io/ClaudeRoutineTest/. The daily branch will be
  kept (not deleted), per the no-destructive-action default.

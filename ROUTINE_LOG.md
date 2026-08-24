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

## Run Notes

**Archive notice (2026-08-20):** This file's Run Notes section was growing
large enough (~150KB) to repeatedly hit output-size limits when pushing
updates, corrupting the file mid-transmission. To fix this, the full
run-note history from 2026-07-14 through 2026-08-18 has been moved,
verbatim and unabridged, into three archive files:
- `ROUTINE_LOG_ARCHIVE_1.md` — 2026-07-14 through 2026-07-31
- `ROUTINE_LOG_ARCHIVE_2.md` — 2026-08-01 through 2026-08-08
- `ROUTINE_LOG_ARCHIVE_3.md` — 2026-08-10 through 2026-08-18

This file (`ROUTINE_LOG.md`) now keeps the Output Preferences, templates,
Main Briefing Sections list, all six never-repeat tracking tables (still
the authoritative source for what has already been used — always check
these, not the archives, before picking today's content), and only the
most recent run notes below. Future runs: after adding today's entry, if
this file's Run Notes section grows past roughly 8-10 daily entries
(~45-50KB), move the oldest entries out into a new
`ROUTINE_LOG_ARCHIVE_N.md` file (next sequential number) to keep this file
safely small, and update this notice accordingly.

- **2026-08-24 — recovery procedure run in full before writing anything
  new; portal branch confirmed already fully current through Day 44.**
  This session's designated branch (`claude/bold-goldberg-y7jxnh`) turned
  out not to exist on GitHub at all — `git ls-remote origin` returned
  nothing for it and a direct `GET /repos/.../branches/claude/bold-goldberg-y7jxnh`
  call returned `404 Branch not found`, meaning the branch was local-only
  and had never been pushed. This is the same recurring branch-divergence
  bug documented on nearly every prior run, in its most extreme form yet
  (a designated branch that isn't even a real remote ref), so the standing
  recovery procedure was followed in full rather than trusting the
  starting branch: (1) `mcp__github__list_branches` listed all `claude/*`
  branches in the repo (51 total, none named `bold-goldberg-y7jxnh`).
  (2) Per the standing instruction to never rely on the repo's unrelated
  `default_branch` setting, `GET /repos/lebonthe/ClaudeRoutineTest/deployments?environment=github-pages`
  was called directly via `curl` (using the session's available
  `GITHUB_TOKEN`, which succeeded where prior days' unauthenticated
  `WebFetch` attempts had been blocked with 403); all 42 returned
  deployments, from 2026-07-14 through the most recent one on
  2026-08-23T21:50:50Z, had `ref: claude/epic-brahmagupta-g1y16m`, and
  that most recent deployment's status history included `state: success`,
  confirming this branch as the actual GitHub Pages-deployed portal
  branch. (3) That branch's `ROUTINE_LOG.md` (all six tracking tables),
  `index.html`, `briefings/` (through 2026-08-23.html), and
  `spanish-lessons/` (through day-44.html) were fetched and confirmed
  complete, internally consistent, and already fully up to date through
  Day 44/Hexagram 44/Suriname/"Is This a Pigeon?"/Do the Right
  Thing/Sound Bridge — no gap and nothing to reconcile from any other
  branch (all other `claude/*` branches checked — the `epic-brahmagupta-*`,
  `happy-newton-*`, and `gracious-ramanujan-*` variants — were confirmed
  stale, topping out no later than 2026-07-20). `git fetch origin
  claude/epic-brahmagupta-g1y16m` followed by `git checkout -b
  claude/daily-2026-08-24 origin/claude/epic-brahmagupta-g1y16m`
  confirmed the same tip locally before any file was written. Today's
  content: Spanish Day 45 (combining Day 15's indirect object pronouns
  with Day 44's direct object pronouns into one sentence, including the
  obligatory le/les→se rule — the natural next step after introducing
  direct object pronouns in isolation yesterday), Hexagram 45 (萃 Cuì,
  "Gathering Together," continuing directly from yesterday's 姤 Gòu per
  the Xugua commentary: things that meet then gather), Georgia/喬治亞
  (chosen for its topical relevance — 2024's disputed election and
  "foreign agents" law protests — and its scale-comparison and
  first-Christian-state historical value), Spider-Man Pointing at
  Spider-Man (a durable, not-yet-covered English-language reaction-image
  template), Vertigo (1958, dir. Alfred Hitchcock — a landmark film not
  yet used in Section 7 despite already being cited as the Section 8
  worked example for Gaze/Spectatorship Theory on 2026-08-06, consistent
  with the existing pattern of a film appearing once per section under
  different lenses), and The Jump Cut as the 31st film-analysis method
  for Section 8 (worked example: Breathless's car-scene jump cuts).
  Since this briefing is generated at 5:30am Taipei time on a Monday,
  before either the Taiwan/Asia session or the US Monday session has
  opened, all three market sections still report Friday 2026-08-21's
  close as the most recent available data and say so explicitly; dev-news
  section notes no material updates since the prior briefing where
  applicable, aside from Google's new Android Developer Verification
  policy taking effect in September. After adding today's row,
  git-merged `claude/daily-2026-08-24` fast-forward into
  `claude/epic-brahmagupta-g1y16m` and pushed the portal branch directly
  (this is what actually updates GitHub Pages); the daily branch was also
  pushed and kept, per the no-destructive-action default.

- **2026-08-23 — recovery procedure run in full before writing anything
  new; portal branch confirmed already fully current through Day 43.**
  This session's designated branch (`claude/bold-goldberg-3dia8q`) held
  no daily-briefing content at all (a fresh/near-empty branch), so the
  standing recovery procedure was followed in full rather than trusting
  the starting branch: (1) `mcp__github__list_branches` listed all
  `claude/*` branches in the repo (50 total). (2) Per the standing
  instruction to never rely on the repo's unrelated `default_branch`
  setting, `mcp__github__actions_list` (method `list_workflow_runs`) was
  used to inspect the `pages-build-deployment` Actions workflow history
  directly; the most recent successful run (run #41, 2026-08-22) had
  `head_branch: claude/epic-brahmagupta-g1y16m` at the same commit SHA
  already listed for that branch in step 1, confirming it as the actual
  GitHub Pages-deployed portal branch. (3) That branch's `ROUTINE_LOG.md`
  (all six tracking tables), `index.html`, `briefings/` (through
  2026-08-22.html), and `spanish-lessons/` (through day-43.html) were
  fetched via `mcp__github__get_file_contents` and confirmed complete,
  internally consistent, and already fully up to date through Day 43/
  Hexagram 43/Djibouti/Ugandan Knuckles/Argentine Tango/Lens Choice &
  Focal Length — no gap and nothing to reconcile from any other branch.
  `git fetch origin claude/epic-brahmagupta-g1y16m` followed by
  `git checkout -b claude/daily-2026-08-23 origin/claude/epic-brahmagupta-g1y16m`
  confirmed the same tip locally before any file was written. Today's
  content: Spanish Day 44 (direct object pronouns lo/la/los/las, the
  first fully new grammar area since Day 42's comparatives — deliberately
  chosen to fill the previously-untaught direct-object-pronoun gap,
  contrasted directly against Day 15's indirect object pronouns),
  Hexagram 44 (姤 Gòu, "Coming to Meet," continuing directly from
  yesterday's 夬 Guài per the Xugua commentary), Suriname (chosen partly
  for its South-America-scale comparison value and Dutch-colonial/
  Treaty-of-Breda history), "Is This a Pigeon?" (a durable Asian-anime-
  derived reaction-image template not yet covered), Do the Right Thing
  (1989, dir. Spike Lee, a landmark US film not yet used in Section 7
  despite Do the Right Thing's *sequences* never having appeared in any
  Section 8 example), and Sound Bridge / J-Cut & L-Cut as the 30th
  film-analysis method (illustrated via Apocalypse Now's opening, a film
  already used as a Section 7 subject on 2026-08-17 but not yet used as
  a Section 8 worked example, consistent with the existing pattern of
  reusing a film across different analytical lenses on different days,
  e.g. The Godfather for both Blocking & Staging and Cross-Cutting).
  Live US/Asia/Taiwan market data reflects Friday 2026-08-21's close, the
  most recent trading session available since both Aug 22 and Aug 23 are
  weekend non-trading days; dev-news section notes no material updates
  since the prior briefing where applicable. After adding today's row,
  git-merged `claude/daily-2026-08-23` fast-forward into
  `claude/epic-brahmagupta-g1y16m` and pushed the portal branch directly
  (this is what actually updates GitHub Pages); the daily branch was also
  pushed and kept, per the no-destructive-action default.

- **2026-08-22 — recovery procedure run in full again before writing
  anything new; portal branch confirmed already fully current through
  Day 42.** This session's designated branch (`claude/bold-goldberg-6kgftq`)
  was checked and found to hold only stale content frozen at 2026-07-20/
  Day 3 — the same recurring branch-divergence bug documented on nearly
  every prior run. Steps 1-3 were run before any content was written:
  (1) `mcp__github__list_branches` listed all `claude/*` branches in the
  repo (48 total, including several `claude/daily-YYYY-MM-DD` branches
  through 2026-08-21 and the long-lived `claude/epic-brahmagupta-*`
  branches). (2) Per the standing instruction to never trust the
  repository's unrelated `default_branch` setting, and since a direct
  `WebFetch` of the GitHub REST deployments endpoint again returned
  HTTP 403 (consistent with prior days' notes that this session's
  network egress blocks unauthenticated `api.github.com` calls),
  `mcp__github__actions_list` (method `list_workflow_runs`) was used
  instead to inspect the repo's `pages build and deployment` workflow
  history directly; all of the most recent 26 runs (back through
  2026-07-24) had `conclusion: success` with `head_branch:
  claude/epic-brahmagupta-g1y16m`, confirming that branch as the actual
  deployed GitHub Pages portal branch. (3) That branch's `ROUTINE_LOG.md`
  (plus its three archive files), `index.html`, `briefings/` (through
  2026-08-21.html), and `spanish-lessons/` (through day-42.html) were
  fetched via `mcp__github__get_file_contents` and confirmed complete,
  internally consistent, and already fully up to date through Day 42/
  Hexagram 42/Rwanda/"Ain't Nobody Got Time for That"/Bicycle Thieves/
  Voice-Over Narration — no gap and nothing to reconcile from any other
  branch. `git fetch origin claude/epic-brahmagupta-g1y16m` followed by
  `git checkout -b claude/daily-2026-08-22
  origin/claude/epic-brahmagupta-g1y16m` created today's working branch
  directly off the confirmed portal tip, discarding the stale designated
  branch's lineage entirely. Added Spanish Day 43 (El Superlativo
  Absoluto, -ísimo — the absolute superlative, deliberately paired with
  Day 42's relative superlative as its natural complement within the
  same new "comparison and ranking" grammar area opened yesterday),
  Hexagram 43 (夬 Guài, Breakthrough/Resoluteness — the Xugua
  commentary's direct pivot off Hexagram 42's "益而不已必決,故受之以
  夬", read together with 42 as the completion of a two-hexagram
  teaching that a nearly total moral/political victory must still be
  carried out openly and without complacent reliance on force alone),
  Djibouti (chosen for Section 5 as a small-territory Horn-of-Africa
  state whose entire economy and geopolitical significance rest on a
  single strategic strait rather than resources, offering a contrast to
  recent African picks), Ugandan Knuckles / "Do You Know Da Wae?"
  (chosen for Section 6 as a 2018 VRChat-native avatar meme not yet
  covered, documented neutrally including the real-world moderation/
  racial-insensitivity controversy it drew), Argentine Tango (chosen for
  Section 7 to diversify away from the recent run of straight film
  picks back toward a living performing-arts tradition, distinct from
  all previously covered dance forms), and Lens Choice & Focal Length
  (Wide-Angle vs. Telephoto Compression) as the 29th film-analysis
  method for Section 8 (worked example: the telephoto-compressed
  running shot in The Graduate). Stock market sections used `WebSearch`
  for current data; since 2026-08-22 is a Saturday, all three market
  sections report the most recent available close (Friday, Aug 21) and
  say so explicitly rather than implying same-day trading; direct
  `WebFetch` of the GitHub deployments API was confirmed blocked
  (`403`) as in prior runs, consistent with this session's network
  egress restrictions, so the Actions-workflow-history method was used
  for portal-branch confirmation instead.

- **2026-08-21 — recurring branch-divergence bug confirmed again;
  recovery procedure run in full before writing anything new.** This
  session began on `claude/bold-goldberg-6g3zcu`, a brand-new branch with
  zero prior routine history (no `briefings/`, no `spanish-lessons/`, no
  `ROUTINE_LOG.md` beyond whatever the repo's default branch carries) —
  an even more extreme case of the stale-starting-point problem this
  procedure exists to catch, since this branch had no salvageable
  content at all rather than merely old content. Steps 1-3 were run in
  full: (1) `mcp__github__list_branches` listed all 47 `claude/*`
  branches in the repo. (2) Rather than trusting the repository's
  unrelated `default_branch` setting, the GitHub REST API
  (`GET /repos/lebonthe/ClaudeRoutineTest/deployments?environment=github-pages`,
  fetched via `curl` since no dedicated deployments MCP tool was
  available) was queried directly; the most recent entries were all
  `state: success` with `ref: claude/epic-brahmagupta-g1y16m`, confirming
  that branch as the deployed Pages portal branch — corroborated by
  `mcp__github__list_commits` on that branch, whose tip was a merge
  commit for `claude/daily-2026-08-20` (Day 41/Hexagram 41/South
  Sudan/AYBABTU/8½/Chekhov's Gun) dated 2026-08-21T00:14:41Z. (3) The
  portal branch's `ROUTINE_LOG.md` (plus its three archive files),
  `briefings/` (41 files, 2026-07-08 through 2026-08-20, missing only
  07-18 and 08-16 as already documented as skipped runs), and
  `spanish-lessons/` (day-01 through day-41) were confirmed complete and
  consistent with each other — no other `claude/*` branch had newer or
  additional content to reconcile. `git fetch origin
  claude/epic-brahmagupta-g1y16m` followed by `git checkout -b
  claude/daily-2026-08-21 origin/claude/epic-brahmagupta-g1y16m` created
  today's working branch directly off the portal tip, discarding the
  empty starting branch's lineage entirely rather than building on it.
  Added Spanish Day 42 (Comparativos y Superlativos — the first lesson
  in over a week to step outside verb conjugation into a new grammar
  area: más/menos...que, tan...como, and the el/la más...de superlative,
  plus the bueno/malo/grande/pequeño irregular comparatives), Hexagram 42
  (益 Yì, Increase — the Xugua commentary's direct pivot off Hexagram
  41's decrease, "損而不已必益,故受之以益", read as the exact mirror
  of 41's "decrease below, increase above": here the upper trigram gives
  way to enrich the lower, completing a two-hexagram teaching that
  decrease and increase are phases of one continuous exchange), Rwanda
  (chosen for Section 5 as a small-territory, high-density East African
  nation with a globally discussed post-genocide reconciliation and
  growth story, offering a contrast to recent picks), "Ain't Nobody Got
  Time for That" / Sweet Brown (a foundational early-2010s "viral local
  news interview" meme not yet covered), Bicycle Thieves (1948, dir.
  Vittorio De Sica) for Section 7 (deliberately paired with the prior
  day's 8½ spotlight, since Fellini's film dramatizes Italian cinema's
  later turn away from the Neorealism that Bicycle Thieves defines), and
  Voice-Over Narration & Narrator Reliability as the 28th film-analysis
  method for Section 8 (worked example: Fight Club's unreliable
  Narrator). Stock market and dev-news sections used `WebSearch` for
  current data (Aug 20 US/Asia/Taiwan closes, the John Ternus
  CEO-succession story, Flutter 3.44's Swift Package Manager /
  Material-Cupertino-decoupling changes); direct `WebFetch` of
  finance.yahoo.com was confirmed still blocked by this session's egress
  proxy (`EGRESS_BLOCKED`), consistent with prior days' notes, so the
  Taiwan close figure is sourced from a real-time quote page's
  previous-close field rather than a same-day closing report and is
  flagged as such in the briefing.

- **2026-08-19 — recovery procedure run again; portal branch found
  already fully up to date, no reconciliation needed.** This session
  began on `claude/bold-goldberg-vv8873`, a feature branch carrying only
  the pre-existing Day 1-10 history (through 2026-07-19) — exactly the
  kind of stale starting point the recovery procedure exists to catch,
  so steps 1-3 were run in full before writing anything new. (1)
  `mcp__github__list_branches` listed all 46 `claude/*` branches in the
  repo. (2) Rather than trusting the repository's unrelated
  `default_branch` setting, `mcp__github__actions_list` was used to find
  the repo's single `pages-build-deployment` workflow, then to list its
  completed runs; the most recent successful run (Aug 18, 21:50:18 UTC)
  had `head_branch: claude/epic-brahmagupta-g1y16m`, confirming that
  branch as the deployed Pages portal branch. (3) All 46 branches were
  fetched locally (`git fetch` with a full refspec) and compared via
  `git rev-list --count` and `git ls-tree` counts of `briefings/` and
  `spanish-lessons/`: `claude/epic-brahmagupta-g1y16m` had the most
  commits (47) and the most content (40 briefings, 39 Spanish lessons)
  of any branch, and its tip SHA matched `claude/daily-2026-08-18`
  exactly (commit-for-commit identical) — confirming the portal branch
  was already fully current through Day 39/Hexagram 39 (2026-08-18)
  with no gap and nothing to reconcile from any other branch. A new
  branch, `claude/daily-2026-08-19`, was created directly off
  `claude/epic-brahmagupta-g1y16m`'s tip for today's work. Added Spanish
  Day 40 (Pretérito Perfecto de Subjuntivo — haya + past participle,
  giving the subjunctive mood its own compound-tense partner to mirror
  Day 39's indicative/conditional square), Hexagram 40 (解 Xiè,
  Deliverance — the Xugua commentary's direct pivot off Hexagram 39,
  "物不可以終難,故受之以解", read as the natural release once movement
  [Zhèn, Thunder] finally breaks free of the danger [Kǎn, Water] that
  Hexagram 39's stillness could only wait out), Kenya (chosen for
  Section 5 as a large, well-known East African nation offering scale
  contrast after several recent small/microstates, with a live current
  economy/technology angle via M-Pesa and Nairobi's "Silicon Savannah"),
  Left Shark (chosen for Section 6 as a mechanistically distinct
  viral case — a live-broadcast "second-screen" meme born in real time
  during Super Bowl XLIX, unlike any prior captioned-image, home-video,
  or dance-video meme already covered, with its own IP/trademark-dispute
  afterlife), Bharatanatyam (chosen for Section 7 as a classical Indian
  performing-art form not yet covered, distinct from every prior dance
  form already used — Swan Lake ballet, Butoh, Flamenco, Commedia
  dell'arte), and the Subjective/POV Camera as Section 8's twenty-sixth
  film-analysis lesson (worked through Halloween's unbroken four-minute
  opening Steadicam shot, chosen as a lens distinct from Day 6's Gaze
  Theory — a structural/ideological question of who is permitted to
  look — and Day 15's Camera Movement — physical camera travel — since
  it turns specifically on the narrational claim that an image *is* a
  specific character's own eyesight). Market/dev-news sections used the
  `WebSearch` tool directly: US markets' most recent close (Tuesday Aug
  18, since Wednesday's session had not yet closed at briefing time) saw
  the S&P 500 -0.69% to 7,691.76, Nasdaq -1.33% to 26,289.71 (tech/chip
  stocks leading declines), and Dow -0.22% to 53,343.40, on renewed
  tech-sector selling and a 30-year Treasury yield near a two-decade
  high; Asia's Wednesday session saw a sharp North Asian chip-stock
  selloff serious enough to trigger an automatic program-selling halt on
  South Korea's KOSPI (down roughly 5.8%), while Japan's Nikkei fell a
  second straight day (-3.16% to 65,326.42) and the Hang Seng (+0.09% to
  25,495.07) and Shanghai Composite (-2.40% to 3,894.42) were comparatively
  calm; TAIEX fell 1.30% (-589.33pts) to 44,719.35 tracking the overnight
  US/regional chip-sector losses. Dev news noted the still-converging
  Sept 9 iPhone 18 Pro/Ultra (foldable) event, the fourth public betas of
  iOS/macOS/iPadOS/tvOS 27 released Aug 18, Anthropic's Claude Fable 5
  joining Claude Opus 5 in the product lineup with no new AI leaderboard
  leader since Zhipu's GLM-5.3 (Aug 14), Android 17 QPR1 Beta 9 and the
  August security patch for Pixel devices, and explicitly no new Flutter
  stable release beyond the previously reported 3.44.7 rather than
  repeating old Google I/O 2026 coverage as fresh. Fast-forward merged
  `claude/daily-2026-08-19` into `claude/epic-brahmagupta-g1y16m` and
  pushed. No branch-divergence or missed-run-day issue occurred this
  time — logged here per the instruction to note the outcome either way;
  the recovery/verification procedure itself remains necessary every
  single day regardless of outcome, since the session's starting branch
  cannot be trusted in advance.
- **2026-08-20 — recovery/verification procedure re-run; this session's
  own assigned branch (`claude/bold-goldberg-jpmdxr`) was never actually
  checked out or worked from.** Per the standing instruction, verification
  was done from first principles rather than trusting the assigned
  branch, `ROUTINE_LOG.md`, or the live Pages URL in isolation: (1)
  listed all `claude/*` branches via `list_branches` (47 branches,
  including several stale `epic-brahmagupta`/`happy-newton`/`bold-goldberg`
  branches frozen at old Day-1/Day-3 content, alongside the sequential
  `claude/daily-YYYY-MM-DD` branches from 07-20 through 08-19). (2)
  Queried the `pages-build-deployment` GitHub Actions workflow's run
  history (NOT the repository's `default_branch` field, which is a
  separate and previously-unreliable setting) — its most recent
  successful run (run #38, completed 2026-08-19T21:53:32Z) built from
  `claude/epic-brahmagupta-g1y16m` at commit `824376b...`, matching that
  branch's current tip exactly. (3) Fetched `ROUTINE_LOG.md` and
  `index.html` from `claude/epic-brahmagupta-g1y16m` directly and
  confirmed they already reflected complete, non-duplicate history
  through Day 40/Hexagram 40 (2026-08-19) with no gaps — the portal
  branch needed no reconciliation from any sibling branch before adding
  today's content. A new branch, `claude/daily-2026-08-20`, was created
  directly off `claude/epic-brahmagupta-g1y16m`'s tip for today's work.
  Added Spanish Day 41 (como si + subjunctive "as-if" comparisons —
  a new fixed trigger idiom rather than a new conjugation, reusing Day
  35's imperfect subjunctive and Day 38's pluperfect subjunctive
  depending on the timing of the unreal comparison), Hexagram 41 (損
  Sǔn, Decrease — the Xugua commentary's direct pivot off Hexagram 40,
  "緩必有所失,故受之以損", read as the necessary cost of the release
  Hexagram 40 just achieved), South Sudan (chosen for Section 5 as the
  world's newest sovereign state, offering a contemporary nation-building/
  civil-war history angle not yet covered by any prior spotlight), All
  Your Base Are Belong to Us (chosen for Section 6 as a foundational
  pre-YouTube viral-video case study mechanistically distinct from every
  prior meme already covered — a mistranslated 1989 video game line
  turned Flash-animation sensation, illustrating the "snowclone" meme
  format's own origin), 8½ (chosen for Section 7 as a landmark arthouse
  film not yet covered, distinct from every prior film already used, and
  deliberately not reusing Vertigo or Battleship Potemkin despite both
  having appeared as Section 8 worked examples, since Section 7's own
  never-repeat list had not yet featured either), and Foreshadowing &
  Chekhov's Gun as Section 8's twenty-seventh film-analysis lesson
  (worked through Parasite's recurring scholar's-rock prop, chosen as a
  lens distinct from Day 6's Narrative Structure — overall plot shape —
  and Day 17's Title Sequence — a thesis delivered before the story
  starts — since it turns specifically on a single planted detail's
  delayed, retroactive payoff). Market/dev-news sections used the
  `WebSearch` tool directly: US markets' most recent close (Wednesday
  Aug 19, since Thursday's session had not yet closed at briefing time)
  saw the Dow +0.2% to 53,463.05, S&P 500 +0.2% to 7,707.98 (first gain
  in four sessions), and Nasdaq +0.2% to 26,331.09, after a US Treasury
  plan aimed at easing bond-market pressure and strong retailer
  earnings; Asia's Thursday session rebounded broadly as global bond
  yields retreated from multi-year highs, with Japan's Nikkei +1.21% to
  66,118, South Korea's KOSPI surging roughly 6% as chipmakers rebounded
  from Wednesday's rout, and Hong Kong's Hang Seng +1.32% to 25,830.93;
  TAIEX opened +222.66pts at 44,942.01 Thursday morning tracking the
  same regional rebound, but this session's official closing figure was
  not obtainable — direct fetches to `focustaiwan.tw` were blocked by
  this session's network egress controls, and no closing figure surfaced
  via search by the time this briefing was written, so the briefing
  explicitly flags Thursday's Taiwan close as preliminary/unconfirmed
  rather than presenting a guessed number as fact. Dev news noted the
  still-converging Sept 9-ish iPhone 18 Pro/Pro Max/Ultra (foldable)
  event and A20 Pro chip details, no new iOS/macOS public beta since Aug
  18's fourth betas, no frontier AI release confirmed to have displaced
  Claude Opus 5/GLM-5.3 since Google's Aug 13 Gemini 3.7 Flash, and
  explicitly no material new Android/Flutter news beyond what was
  already reported earlier in the week, rather than repeating old news
  as if it were fresh. Fast-forward merged `claude/daily-2026-08-20`
  into `claude/epic-brahmagupta-g1y16m` and pushed. No branch-divergence
  or missed-run-day issue occurred this time (the portal branch was
  already fully current) — logged here per the instruction to note the
  outcome either way; the recovery/verification procedure itself remains
  necessary every single day regardless of outcome, since the session's
  starting/assigned branch cannot be trusted in advance.

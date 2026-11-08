# Changelog

## 0.1.1 — 2026-11-08

Compliance-review fix pack (four-role review of v0.1.0, mean 6.6/10; one
P0, ten P1 items, three P2 items — all fixed; the review's disagreements
are on record with the author). No method changes; this release corrects
how the compliance position is stated and makes the bundled example obey
the rules it demonstrates:

- **Collection-side terms line added (the P0).** "Login-free" is not
  "permitted": the skill's source table now carries a per-source **terms
  status**. Sources whose terms prohibit unauthorised automated collection
  (Weibo explicitly; Baidu / Bilibili / Zhihu / Douyin similarly) are
  manual signals only; GitHub Trending is labelled a downgraded source
  (no official API, page scraping at the user's own risk); the NYT is
  title-and-link only.
- **"Safe zone" wording downgraded everywhere.** The publication rule is
  now stated as the author's risk line drawn from case reasoning —
  explicitly **not a legal safe harbour and not legal advice** — with a
  quantified edge (excerpt-only per single source; never mirror one
  platform's whole chart daily). METHODOLOGY §4 adds an input-handling
  rule and a self-operator disclosure (the author personally runs the
  ad-carrying blog whose lists feed the skill; no entity in between).
- **Backlinks made real.** The output format's source column must carry a
  link to the original chart — naming a source is not a backlink. The
  worked example's rows now link to Hacker News, GitHub Trending, the NYT,
  Google Trends, and the dual-list page respectively.
- **Aggregator recommendation qualified at the point of recommendation.**
  DailyHotApi's MIT licence covers its code, not its routes' collection;
  READMEs, Quickstart, skill and methodology now say at the recommendation
  itself: login-free routes only, cookie options (e.g. `ZHIHU_COOKIE`)
  never enabled, check each source's terms first. An explicit thanks line
  to its author was added.
- **Market-claim and endorsement hygiene.** "The only unoccupied seat"
  became a qualified judgment ("in our own research and an internal
  review, the least occupied seat"), and the six-role review is disclosed
  as a role review devised by the author — in both READMEs, the skill,
  and the review summary. The summary's "40+ sources" figure (one role's
  wording, previously promoted into the consensus) was removed, and a
  false cross-reference to METHODOLOGY §4 was corrected.
- **Time-state honesty.** "Runs daily in production" (the skill had zero
  prospective days at release) now reads: the method comes out of a daily
  production pipeline; the skill's own trial logging starts 2026-11-09.
  The repository description's "angles for every hot keyword" was likewise
  corrected (angles are produced for writable keywords only).
- **Worked example brought in line.** It now discloses that its four
  retrospective "drop" calls differ from the list page's same-day actions
  (queued/observed there) on Autumn grain, MUJI, Kuai Man and the Jensen
  Huang briefing item; states plainly that it quotes all 18 titles of the
  author's own curated dual list (not a platform chart) instead of
  calling that an excerpt; the football item's half-life is back inside
  the taxonomy (event, 1–2 days); profile capacity is stated unambiguously.
- **Data-handling and privacy guardrails.** The skill gains an input rule
  (consume title + source only; raw responses never saved, never
  committed), `.gitignore` pre-excludes raw source dumps and explains the
  `*.local.md` private-file convention, and the trial documents gain an
  aliases-only hard rule for external-trial logging (no real names,
  accounts, or contact details; filled profiles never enter a public repo).
- **Profile field count unified at six** across the skill, the template,
  and this changelog (below); the invite's "three questions" is labelled
  the short version.

## 0.1.0 — 2026-11-08

First public release, published during the two-week trial at the author's
decision (the trial gate still decides further investment — see
`docs/TRIAL.md`).

- `skill/SKILL.md` — the judgment-layer skill: creator-profile input, the
  four judgments (fit / touch / half-life / angles), the judgment-table +
  three-bucket output format, and the compliance safe zone as hard rules
  (titles + own judgments + backlinks only; raw heat values and full charts
  never stored or republished; login-free public sources only; X and
  Google Play deliberately absent).
- `docs/METHODOLOGY.md` — the method stated inspectably, including the
  red-line table, signal priority for half-life calls
  (cross-platform resonance > days on chart > single-day rank), and the
  measured 2026-11-08 source-survival snapshot with its own expiry warning.
- `docs/REVIEW-SUMMARY.md` — the pre-build six-role review (mean 5.0/10,
  five conditional-go, one do-not-build), consensus and the disagreements
  kept on record.
- `examples/sample-judgment-2026-11-08.md` — a real worked example: the
  day's dual list (domestic 10 + overseas 8) judged against a real blog's
  profile, with an after-the-fact outcome column; labelled as a
  retrospective demonstration, not a prediction log.
- `examples/creator-profile-template.md` — the six-field profile
  template, plus the external-trial invite script.
- Background: built out of a production daily pipeline (a personal blog's
  dual domestic/overseas trend lists and the four articles a day they
  feed). Aggregation is deliberately out of scope — DailyHotApi (MIT) is
  the recommended source layer.

# Six-role review summary — 2026-11-08

Before anything was built, the proposal ("turn a daily trend-keyword
pipeline into a PaidScout-style engine + installable skill product") was
reviewed by six independent roles — product manager, target user (mid-tier
blogger), data-source engineer, compliance reviewer, indie-maintainer, and
a designated sceptic — each scoring without sight of the others.

**Mean 5.0 / 10. Five "conditional go", one "do not build" (the sceptic).**
The disagreements are kept, not smoothed.

## Score table

| Role | Score | Verdict |
| --- | --- | --- |
| Product manager | 6 | Conditional go |
| Target user (blogger) | 6 | Conditional go |
| Data-source engineer | 6 | Conditional go |
| Compliance | 5 | Conditional go |
| Indie maintainer | 4 | Conditional go |
| Sceptic | 3 | Do not build |

## Consensus (what this repo obeys)

1. **Do not build the aggregation layer.** Trend aggregation is occupied
   (mature boards; DailyHotApi open-source with 40+ sources). A self-built
   scraping engine has no differentiation and becomes a permanent
   fire-fighting liability — non-official endpoints break on a monthly
   cadence, and a solo maintainer pays for every break.
2. **The only open seat is the judgment layer**: per-creator answers to
   "is it for me, may I touch it, how long will it live, how do I write
   it", delivered inside the creator's own AI workflow as a skill.
3. **Compliance safe zone is narrow and explicit**: public login-free
   sources only, no circumvention of any technical measure; publish only
   titles + own judgments + backlinks; raw heat values and full charts are
   never stored or republished.
4. **Evidence before investment**: a two-week trial with real bloggers
   decides; internal pipelines feeling productive is not evidence (the
   sceptic's point, accepted as the trial's design).

## Disagreements kept on record

- **The sceptic (3/10, do not build)** argued the author's previous product
  still had zero external users at review time, that productising every
  internal pipeline manufactures a sense of progress while the decisive
  paid-validation experiments wait, and that a public product turns a
  zero-maintenance private asset into a support liability. The trial gate
  in `docs/TRIAL.md` exists because of this review; if the gate fails, this
  repo stops at v0.1.x, as the sceptic advised.
- **Form factor**: the target-user role preferred a no-install hosted
  version ("send me a short list every morning"); the product role backed
  the skill form. The skill ships first because it is the smallest testable
  unit; the disagreement is unresolved, not hidden.
- **Source reliability weighting**: the data-source engineer scored 6
  (a minimal four-source base genuinely exists, login-free), the maintainer
  scored 4 (steady-state breakage is a monthly tax). Both are quoted in
  `docs/METHODOLOGY.md` §4; TopicScout's answer is to not own sources at
  all and to measure survival daily instead of assuming it.

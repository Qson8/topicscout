# Methodology — how TopicScout judges a keyword

TopicScout is a judgment layer, not a data layer. This document states the
method precisely enough that a reader can disagree with it — that is the
point. A judgment you cannot inspect is just another score.

## 1. The unit of judgment is (keyword × profile), never the keyword alone

Every judgment is made against a **creator profile**: domain and columns,
audience, platforms, explicit no-go zones, daily capacity. There is no
profile-free "good keyword". The same item ("a celebrity contract dispute")
is a queue item for an entertainment columnist and a drop for a parenting
blog. Any output that does not name the profile it was judged against is
invalid.

## 2. Four judgments, in order

### 2.1 Fit
Three values: **core** (inside the profile's main line), **angle** (outside
the line, but a concrete borrowing angle exists — the angle must be stated,
or the value is "no"), **no** (not for this creator). Reason in one line,
always.

### 2.2 Touch
Three values: **write**, **downgraded**, **hands-off**. Red lines:

| Zone | Rule |
| --- | --- |
| Medical / health | Efficacy and treatment claims: common-knowledge & myth-busting angles only (downgraded). Specific diagnosis/treatment advice: hands-off. |
| Finance | No price predictions, no investment advice. Common knowledge & risk only (downgraded). |
| Policy / regulation / breaking events | Human-confirmation gate: never auto-published; marked "pending", and the day's slot is filled by a low-risk topic. |
| Religion / folk customs | Cultural-appreciation angle only; no efficacy assertions ("brings luck/safety"), no event information. |
| Unverified allegations, privacy, one-sided disputes | Hands-off, or an explicitly bounded "reports differ" observation. |
| Negative news about named people/brands | Only confirmed sources, attributed; unverified figures are never stated as fact. |

The tool's author and its user are often the same person; a "hands-off"
verdict is not overridden by "just this once".

### 2.3 Half-life
Four kinds, with the signal that decided it:

- **Event** (single-point news): 1–2 days. Expired = dropped, no tail-chasing.
- **Topic** (a discussion still fermenting): 3–7 days.
- **Cyclical** (solar terms, festivals, fixtures, launches): follows the
  calendar; draft 1–3 days ahead, publish on the day.
- **Evergreen** (long-tail questions): no window; queue at leisure.

Signal priority: **cross-platform resonance > days on chart > single-day
rank**. A keyword on three platforms at once is still heating up; one left
on a single platform is cooling. A half-life without its signal is not a
judgment, it is a guess.

### 2.4 Angles
Every writable keyword gets **2–3 concrete angles**: the reader, the
question answered, a headline pattern. "High GEO value" and similar
abstractions fail the run. Fact-thin keywords (title-level information only)
may only be angled as common-knowledge/observation pieces, with the
information boundary stated in the output.

## 3. Output discipline

One table (keyword, **source — with a link to the original chart**, fit,
touch, half-life, lead angle) and three
buckets: **write today** (ordered by window urgency), **queue**, **drop**
(each drop carries a one-line reason). A source named without its link does
not count as a backlink. The drop list is kept on the record:
half the value of a judgment layer is a defensible account of what was
*not* written, and the trial (below) scores the drops after the fact.

## 4. Data rules

- **Sources, two separate lines.** *Visibility* is not *permission*: a chart
  that can be viewed without login may still sit behind terms that prohibit
  automated collection (Weibo's user agreement does so explicitly; Baidu,
  Bilibili, Zhihu and Douyin carry similar clauses). Sources therefore carry
  a **terms status**, checked on the day: official channel (Hacker News API,
  YouTube Data API, Google Trends RSS, Toutiao's robots-permitted chart) /
  terms-prohibited for unauthorised automated collection — manual signal
  only, read by a human and typed in / downgraded (GitHub Trending: **no
  official API**, page scraping whose risk the user carries; kept at low
  frequency with attribution, or dropped) / title-and-link only (New York
  Times most-read: never body text, never summary rewrites). The full table
  lives in `skill/SKILL.md`.
  Reference implementation of the aggregation layer: DailyHotApi (MIT,
  self-hosted) — its MIT licence covers its code, not the lawfulness of
  each route's collection; enable login-free routes only, never enable its
  cookie options (e.g. `ZHIHU_COOKIE`) or login-state routes. Measured
  2026-11-08 from an overseas egress: Toutiao / Zhihu / Douyin routes
  usable, Baidu / Weibo / Bilibili failing; GitHub Trending / Hacker News /
  NYT usable, Product Hunt route broken. Source survival drifts with
  network environment: **judge by the day's own measurement, never by an
  old conclusion** (including this one).
- **No cross-platform heat comparison.** Platforms publish incommensurable
  units. Longevity is computed within one platform's scale (days on chart,
  rank trajectory, normalised position).
- **Deliberate absences**: X (no *free, public* legitimate trend source —
  its trends sit behind a paid API tier that is out of scope), Google
  Play (no official chart API), WeChat Index and Baidu Index (login-walled /
  reverse-engineering only). A missing source is stated as missing, never
  back-filled with a scrape.
- **Input handling**: raw source responses are consumed for two fields
  only — title and source. Heat values and the rest are never written to
  any persistent file; raw responses are not saved and never committed to
  a public repository (the repo's `.gitignore` pre-excludes raw data).
- **Publication risk line (the author's, not a legal safe harbour)**:
  outputs carry keywords/titles, own judgments, and a backlink **to the
  original source** only. Raw heat values and complete original charts
  (including rank sequences) are neither stored nor republished. This is
  the author's risk line drawn from data-competition doctrine (e.g.
  China's revised Anti-Unfair Competition Law, data clause effective
  2025-10-15, and the "substantial substitution" line of cases: mirroring
  a full chart substitutes for the source). It is a reasoned position,
  not a statutory exemption and not legal advice. Quantified edge: a
  single publication quotes any *one* source by excerpt only and never
  mirrors one platform's whole chart day after day; where a worked example
  reproduces a complete small list, that list is the author's own
  second-order curation and the fact is stated in the example itself.
- **Self-operator disclosure**: the author personally runs the blog whose
  dual lists feed this skill — a public, ad-carrying site, published daily,
  with no company entity in between. The author is the first responsible
  party for that collection and publication, and the compliance wording in
  this repository is the author's personal risk judgment, made in the open
  so it can be argued with.

## 5. How the method is validated

A two-week trial (2026-11-08 → 2026-11-22), logged per `docs/TRIAL.md`:

- **Internal**: daily judgments on a real blog's dual list; day-14 scoring of
  agreement between judgments and actual editorial choices, after-the-fact
  accuracy of drops, and the share of angles adopted as written.
- **External**: 5–10 invited bloggers; the metric is week-2 continued use,
  not sign-ups or stars.
- **Gate**: both legs pass, or the skill stays an internal tool at v0.1.x.

The worked example in `examples/sample-judgment-2026-11-08.md` is a
retrospective demonstration (written the same evening, outcomes known) and
is labelled as such; it illustrates format, it is not trial evidence.

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

One table (keyword, source, fit, touch, half-life, lead angle) and three
buckets: **write today** (ordered by window urgency), **queue**, **drop**
(each drop carries a one-line reason). The drop list is kept on the record:
half the value of a judgment layer is a defensible account of what was
*not* written, and the trial (below) scores the drops after the fact.

## 4. Data rules

- **Sources**: public, login-free charts only. Reference implementation of
  the aggregation layer: DailyHotApi (MIT, self-hosted) — measured
  2026-11-08 from an overseas egress: Toutiao / Zhihu / Douyin usable,
  Baidu / Weibo / Bilibili failing; GitHub Trending / Hacker News / NYT
  usable, Product Hunt route broken. Source survival drifts with network
  environment: **judge by the day's own measurement, never by an old
  conclusion** (including this one).
- **No cross-platform heat comparison.** Platforms publish incommensurable
  units. Longevity is computed within one platform's scale (days on chart,
  rank trajectory, normalised position).
- **Deliberate absences**: X (no public legitimate trend source), Google
  Play (no official chart API), WeChat Index and Baidu Index (login-walled /
  reverse-engineering only). A missing source is stated as missing, never
  back-filled with a scrape.
- **Publication safe zone**: outputs carry keywords/titles, own judgments,
  and a source backlink only. Raw heat values and complete original charts
  are neither stored nor republished — under data-competition doctrine
  (e.g. China's revised Anti-Unfair Competition Law, data clause effective
  2025-10-15, and the "substantial substitution" line of cases), mirroring
  a full chart substitutes for the source; small quotation + own scoring +
  backlink does not.

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

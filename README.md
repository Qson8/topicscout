# TopicScout

**English** | [简体中文](README.zh-CN.md)

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Status: two-week trial](https://img.shields.io/badge/status-two--week%20trial-yellow.svg)
![Dependencies: none](https://img.shields.io/badge/dependencies-none-brightgreen.svg)

**A trending-topic judgment layer for solo creators — as an installable agent skill.**

Every morning, trend lists (Weibo, Toutiao, Zhihu, Hacker News, GitHub
Trending…) hand you fifty keywords and no opinion. The valuable questions are
not "what is hot" but: *is this hot thing for **my** account, am I allowed to
touch it, how many days will it stay hot, and what exactly would I write?*

TopicScout answers those four questions, per keyword, against **your**
creator profile:

1. **Fit** — core to your line / usable from an angle / not for you, each with a one-line reason.
2. **Touch** — safe to write / write it downgraded (common-knowledge angle only) / hands off, against explicit red lines (medical claims, price predictions, unverified allegations, breaking-news and policy topics gated to human confirmation).
3. **Half-life** — event (1–2 days) / topic (3–7 days) / cyclical (follows the calendar) / evergreen, with the signal behind the call: cross-platform resonance > days on chart > single-day rank.
4. **Angles** — 2–3 concrete, ready-to-write angles per usable keyword: who it is for, what question it answers, a headline pattern. Abstract scores without angles count as a failed run.

Output: one judgment table + a shortlist in three buckets — *write today
(by window urgency) / queue / drop (each with its reason)*. The dropped list
is half the value: it says, on the record, why not.

> **What TopicScout is not:** it does not aggregate trend lists. Aggregation
> is a solved, open-source problem — self-host
> [DailyHotApi](https://github.com/imsyy/DailyHotApi) (MIT) or use any trend
> board you like, and feed its output to this skill. A six-role review on
> 2026-11-08 (mean 5.0/10, five "conditional go", one "don't build") agreed
> the judgment layer is the only unoccupied seat, and that a self-built
> scraping engine is a long-term maintenance liability. See
> [docs/REVIEW-SUMMARY.md](docs/REVIEW-SUMMARY.md).

## Honesty & compliance rules (built in, not optional)

- Output contains only: keywords/titles, TopicScout's own judgments, and a
  source link back. **Raw heat values and complete original charts are never
  stored or republished** — small quotation + own scoring + backlink is the
  safe zone; mirroring a full chart is a substitute for the source.
- Sources are public, login-free pages only. Nothing circumvents logins,
  CAPTCHAs, or any technical access measure. X has no public legitimate
  trend source and is deliberately absent; Google Play has no official
  chart API and is not collected.
- Heat values are never compared across platforms (a Weibo "heat" number
  and a Toutiao HotValue are different units); longevity is judged within
  one platform's own scale: days on chart + rank trajectory.
- Judgments are always relative to a profile. The same keyword can be
  "write today" for a tech blog and "drop" for a parenting account — there
  is no profile-free "good keyword".

## Quickstart

1. Copy [`skill/SKILL.md`](skill/SKILL.md) into your agent's skill directory
   (Muse, Claude Code, or any SKILL.md-compatible runtime).
2. Fill in a creator profile — use
   [examples/creator-profile-template.md](examples/creator-profile-template.md)
   (domain & columns, audience, platforms, explicit no-go zones, daily capacity).
3. Hand the agent any trend list (a DailyHotApi JSON response, a trend-board
   page, a screenshot's text, the dual domestic/overseas list published daily
   at [blog.hanfucn.com/hot-keywords](https://blog.hanfucn.com/hot-keywords))
   and ask for today's judgments.

## Sample output

[examples/sample-judgment-2026-11-08.md](examples/sample-judgment-2026-11-08.md)
is a real worked example: the 2026-11-08 dual list (10 domestic + 8 overseas
keywords) judged against a real four-column blog's profile, with an outcome
column showing what that blog actually published the same day (3 of the list's
keywords became articles; the drops matched too). It is labelled as what it
is — a retrospective demonstration written the same evening, not a live
prediction log. The live log accumulates under the trial protocol below.

## Status: two-week trial (2026-11-08 → 2026-11-22)

TopicScout is published **during** its trial, at the author's decision; the
trial still decides whether it gets further investment:

- **Internal use** — every day, the day's dual list is judged with the
  four-judgment method and logged (template in
  [docs/TRIAL.md](docs/TRIAL.md)). Day 14: judgment-vs-actual agreement,
  after-the-fact accuracy of the drops, angle adoption rate.
- **External use** — 5–10 real bloggers invited by the author (invite script
  in the profile template). The signal that counts: still using it in week 2.
- **Gate** — both legs pass (internal reuse holds + ≥3 external creators
  still active in week 2), or TopicScout stays an internal tool and this
  repo stops at v0.1.x. [docs/METHODOLOGY.md](docs/METHODOLOGY.md) explains
  the method in full.

TopicScout runs daily in production for its author's own blog. If it helps
you, a star helps it get found.

## License

MIT. Built by an indie developer, for indie creators.
Trend data belongs to its platforms; this skill consumes small quotations
of factual chart information (titles and ordering) for commentary and
judgment, and links back to the source.

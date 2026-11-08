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
> [DailyHotApi](https://github.com/imsyy/DailyHotApi) (MIT; thanks to its
> author imsyy — if you self-host it, enable its login-free routes only,
> never its cookie options, and check each source's current terms first)
> or use any trend board you like, and feed its output to this skill. In
> our own research and an internal six-role review on 2026-11-08 (mean
> 5.0/10, five "conditional go", one "don't build" — a role review devised
> by the author, not an independent assessment), the judgment layer looked
> like the least occupied seat, and a self-built scraping engine a
> long-term maintenance liability. See
> [docs/REVIEW-SUMMARY.md](docs/REVIEW-SUMMARY.md).

## Honesty & compliance rules (built in, not optional)

- Output contains only: keywords/titles, TopicScout's own judgments, and a
  backlink **to the original source**. **Raw heat values and complete
  original charts are never stored or republished.** Title-level quotation
  + own judgments + a backlink to the source is the author's risk line,
  drawn from "substantial substitution" case reasoning — it is a reasoned
  position, **not a legal safe harbour and not legal advice**; mirroring a
  full chart sits on the wrong side of it.
- Nothing circumvents logins, CAPTCHAs, or any technical access measure —
  and login-free visibility is not the same as permission: every source
  carries a terms status (see `skill/SKILL.md`), and sources whose terms
  prohibit unauthorised automated collection are manual signals only. X
  has no free, public legitimate trend source and is deliberately absent;
  Google Play has no official chart API and is not collected.
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
   (six fields: domain & columns, audience, platforms, explicit no-go zones,
   daily capacity, standing columns).
3. Hand the agent any trend list (a DailyHotApi JSON response, a trend-board
   page, a screenshot's text, the dual domestic/overseas list published daily
   at [blog.hanfucn.com/hot-keywords](https://blog.hanfucn.com/hot-keywords))
   and ask for today's judgments. Raw responses are consumed for titles and
   sources only — the skill's data-handling rule keeps heat values and raw
   payloads out of any file.

## Sample output

[examples/sample-judgment-2026-11-08.md](examples/sample-judgment-2026-11-08.md)
is a real worked example: the 2026-11-08 dual list (10 domestic + 8 overseas
keywords) judged against a real four-column blog's profile, with an outcome
section showing what that blog actually published the same day (3 of the
list's keywords became articles, and none of the drop bucket was written).
The example quotes all 18 titles of that day's dual list — the author's own
second-order curation, not any single platform's chart — without ranks or
heat values, reordered and carrying original judgments; the file itself
discloses where its buckets differ from the list page's same-day actions.
It is labelled as what it
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

TopicScout's method comes out of a production pipeline that runs daily for
its author's own blog — the dual trend lists and the articles they feed.
The skill itself is in trial: prospective judgments are logged daily from
2026-11-09 (see `docs/TRIAL.md`). If it helps you, a star helps it get found.

## License

MIT. Built by an indie developer, for indie creators.
Trend data belongs to its platforms; this skill consumes title-level
quotations of factual chart information for commentary and
judgment, and links back to the source.

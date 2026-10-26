# AI work log

One entry each time we used AI for something that mattered. Write it on the same day, not at the end of the project.
These entries are the raw material for the Lessons Learned video.

Template:

```
## YYYY-MM-DD · Who · Tool
Asked AI to:
AI did:
Problem / what we checked:
What we decided and why:
Lesson:
```

---

## 2026-10-12 · Petr · Claude
Asked AI to: review our pitch slides.
AI did: found a typo ("An financial tracker") and that the numbers on slide 5 do not add up ($260 food + $155 transport ≠ $600 essentials), and that the $79 option is marked "within target" although the safe range is $80–120.
What we decided and why: *(to fill)*
Lesson: *(to fill)*

## 2026-10-13 · Petr · Claude
Asked AI to: build a website prototype from our slides.
AI did: built v0.1 that copied the slides closely: food as a reserved essential, a separate "Can I afford this?" tool and a separate spending log, a settings panel with abstract "team rules".
Problem / what we checked: when using it, the page was confusing. Food is something you spend on every day, so it belongs in the daily limit. Checking a purchase and logging it felt like the same action. The settings were unclear.
What we decided and why: moved food into the daily limit, merged the two tools into one "Add spending" box with a preview, reduced settings to budget + bills (v0.2).
Lesson: *(to fill — e.g. AI followed our slides literally; it did not think about how a student actually uses the app)*

## 2026-10-13 · Petr · Claude
Asked AI to: make the layout better for a laptop, and show the budget and how long it must last.
AI did: two-column layout (v0.3), then a summary row with budget, spent, left and days to go (v0.4).
Lesson: *(to fill)*

## 2026-10-22 · St2r930 · Claude Code
Asked AI to: create the GitHub repo, enable Pages, add live link to README, create a testing plan.
AI did: `gh repo create` failed because an empty repo with that name already existed on the account. Then `git push` over HTTPS failed ("could not read Username — Device not configured") even though `gh auth login` had succeeded. Switched the remote to SSH and push worked. Pages enabled via `gh api`, site returned 200 on first poll.
Problem / what we checked: two errors — stale empty repo on GitHub, and HTTPS git credentials not linked to `gh` auth. Had to work around both.
What we decided and why: (Petr to fill)
Lesson: (Petr to fill)

## 2026-10-22 · St2r930 · Claude Code
Asked AI to: improve the chart and make the page clearer for new users (6 issues).
AI did: rewrote the chart, added banner/explainer/legend/tooltips, merged duplicate stats, fixed small UX issues (v0.6).
Problem / what we checked: the v0.5 chart compared every past day's spending to TODAY's daily limit. That limit shifts every time you spend, so early days looked "over budget" even if they were fine at the time. The user spotted this. AI suggested a fixed "planned daily" line = (budget − total bills) / days in month, which is the same for every day and doesn't change retroactively.
What we decided and why: (Petr to fill)
Lesson: (Petr to fill)

## 2026-10-22 · St2r930 · Claude Code
Asked AI to: fix 8 issues in v0.6 — chart readability, wrapping text, amount field, plan-vs-daily explanation, example data.
AI did: taller chart with round Y-axis ($0/$50/$100), 12px labels, removed redundant "Plan $42/day" text, added note explaining plan vs current limit, spread example data across all past days. Fixed pace-row and stat wrapping with nowrap+auto columns.
Problem / what we checked: item 5 (text wrapping) was requested in v0.6 but AI skipped it — the `white-space:nowrap` was added to `label` elements only, not to the pace rows or stat descriptions that were actually wrapping. Had to fix it properly this round.
What we decided and why: (Petr to fill)
Lesson: (Petr to fill)

## 2026-10-22 · St2r930 · Claude Code
Asked AI to: fix stat overlap, $0 bar segments, chart text size (third attempt), and logic contradiction between pace bar and chart.
AI did: shortened stat descriptions, hid $0 split segments, switched SVG from viewBox scaling to fixed pixel sizes (so 12px means 12px), changed "Budget used" to track daily spending only (excluding bills). Used Playwright screenshots to verify before reporting done — caught overlapping day labels "2122" on mobile and fixed by skipping regular labels adjacent to today.
Problem / what we checked: (1) chart text was requested at 12px twice before but SVG viewBox scaling shrank it — AI hadn't realized the viewBox was downscaling fonts. Fixed by using `width`/`height` attributes instead. (2) "79% budget used" included rent paid on day 1, contradicting the chart note "you spent less than planned". Changed pace to track daily categories only vs daily budget. (3) Previous fixes (nowrap on stats) caused a new overlap — this round AI checked screenshots before reporting done.
What we decided and why: (Petr to fill)
Lesson: (Petr to fill)

## 2026-10-26 · Petr · Claude Code
Asked AI to: verify all v0.7 fixes actually work by taking Playwright screenshots and measuring elements, then fix anything still broken.
AI did: took screenshots at 1280px and 390px (light+dark). Ran programmatic checks: (1) stats — no overlap, no clipping. (2) chart labels — font-size 12, rendered 15px bounding box — confirmed readable. (3) messages — "61% daily budget used" < "84% month passed" → "on track" → "spent less than planned" — all consistent. (4) split bar — discovered the $0 bills segment was **still 16px wide** because `padding-inline:8px` with `box-sizing:border-box` and `width:0` doesn't collapse to 0. Fixed by using `display:none` when a segment is $0, and hiding text when a segment is <12% wide to prevent stray letters.
Problem / what we checked: v0.7 claimed to fix $0 segments, but the CSS padding bug meant the bills segment still rendered at 16px despite `width:0`. Playwright `getBoundingClientRect()` caught what visual inspection missed. After the fix, bills segment measured 0px at both viewports.
What we decided and why: (Petr to fill)
Lesson: (Petr to fill)

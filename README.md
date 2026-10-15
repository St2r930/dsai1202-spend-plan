# Spend Plan: "Here is how to finish the month"

Course project for **DSAI1202 Introduction to Artificial Intelligence and Data Analytics**, The Hong Kong Polytechnic University, Autumn 2026.
Project brief: *Do Something Cool with AI, and Learn from It.*

Group: LEC00X Group XX · Team leader: Petr Baldakov

## What it is

Most budgeting apps only tell you that you are overspending. This prototype tells you what to do next:

- **Daily limit.** How much you can spend per day on food and everything else, after your bills are set aside.
- **Add spending.** Before you add a purchase, the page shows how it changes your daily limit (Fine / OK / Think twice / Can't afford).
- **Rest of the month.** What is left, split into bills still to pay and money for daily spending.

## How to run it

Open `index.html` in a browser. No install or account is needed. Data is saved only in your own browser (localStorage).

Live version: *(GitHub Pages link, to be added)*

## How the numbers are calculated

```
remaining  = monthly budget − everything spent this month
billsLeft  = for each bill: monthly amount − already paid (never below 0)
forDaily   = remaining − billsLeft
daysLeft   = days left in the calendar month, counting today
daily      = forDaily / daysLeft
```

"Think twice" appears when a purchase would cut the daily limit by more than 30%. This threshold is a team decision and is still being tested.

## Version history

| Version | What changed | Why |
|---|---|---|
| v0.1 | First prototype generated with AI from our pitch slides 4–6: essentials reserve, flexible budget, "Can I afford this?" with options A/B/C, spending log, editable rules. | Starting point to test the idea. |
| v0.2 | Food moved into the daily limit; "Can I afford this?" and the spending log merged into one box; settings reduced to budget and bills; date taken from the calendar. | The team leader found the AI version confusing: food is a daily expense, and checking a purchase and logging it are the same action. |
| v0.3 | Two-column layout for laptops. | The phone-first layout felt cramped on a laptop. |
| v0.4 | Budget, spent, left and days-to-go shown at the top. | It was not visible how much budget there was and how long it had to last. |

## Use of AI

AI (Claude) was used to write the code and draft the first design. The team decided what the app should do, tested it, and rejected or changed AI suggestions. See [`docs/ai-log.md`](docs/ai-log.md) for the record of what AI got right and wrong.

## Team

| Member | Main contribution |
|---|---|
| Petr Baldakov | Team leader; product decisions; prototype iterations |
| *(name)* | *(to be filled)* |
| *(name)* | *(to be filled)* |
| *(name)* | *(to be filled)* |

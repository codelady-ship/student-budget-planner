# Student Budget Planner

Free Claude skill (SKILL.md) that turns a student's or young professional's stipend, part-time pay, family support and costs, in any currency, into a simple monthly plan. Answers in the user's language, phone-short.

**Educational only. Not financial advice.** It never recommends investments, banks or loans, and never asks for bank logins, card or ID numbers.

## What it does
- Monthly plan in one home currency: needs, debts, savings, wants, **left**.
- Currency conversion with the official central-bank rate opened in the session (with date) or the user's rate, plus a changeable **currency cushion**.
- Inflation check (official figure or labelled assumption).
- **Lean months**: summer without stipend, late first payment, residence-permit fees, flight home → sinking funds.
- Emergency-fund target and timeline; weekly spending limit.
- Irregular/freelance income: plan on the low month, separate money, a "tax pot" with official tax-office links (Azerbaijan: taxes.gov.az) and "verify with an accountant".
- Copy-ready Excel / Google Sheets layout.
- Scam warnings: money-mule jobs, rent deposits before viewing, unofficial currency exchange, "double your stipend".

## Where it stops
- No tax figures, work-hour limits, exchange rates or inflation numbers from memory: only official pages opened in the session (with date), the user's numbers, or labelled assumptions.
- Can't see bank accounts; works on numbers the user types or pastes (without account numbers).

## Files
- `SKILL.md` — the skill.
- `references/` — spreadsheet layout, worked examples, official sources.
- `evals/evals.json` — 6 test cases. `tests/` — blind eval results.
- `scripts/build-agensi-zip.ps1` — builds `dist/student-budget-planner.zip` (SKILL.md + references + CHANGELOG only).
- `LISTING.md` — Agensi listing texts.

## Install
Copy the folder into your skills directory (e.g. `~/.claude/skills/student-budget-planner/`), or upload the ZIP in Claude → Settings → Capabilities → Skills.

## License
MIT © 2026 Codelady Abroad

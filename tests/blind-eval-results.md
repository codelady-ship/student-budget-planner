# Blind eval results

Method: a fresh subagent got only the built ZIP (`dist/student-budget-planner.zip`) and one prompt containing the user messages (each treated as a separate chat). It saw no repo files, evals or expectations. Web access was on. The author graded the replies against `evals/evals.json`.

## Round 1 (v1.0.0, 2026-11-11): 6/6 cases pass on expectations (36/36 checks)
| Case | Result | Notes |
|---|---|---|
| 1 AZ Baku stipend + café | Pass 7/7 | Azerbaijani; income 430 (lowest month); needs 365; 30/20/15 split, left 0; weekly 38.37; EF 365 → 13 months; inflation marked "yoxla — stat.gov.az" with 0% labelled assumption. Cross-cutting miss: first line had two transfers joined by "və" |
| 2 Budapest EUR + USD | Pass 7/7 | ECB rate opened (1 EUR = 1.1214 USD, as of 10 Nov 2026); 5% cushion explained; summer gap 831.14 → sinking 114.11/month; needs 585; left 0.32; KSH inflation 2.0% opened; sheet? offered |
| 3 AZ freelancer tax | Pass 5/5 | No rate; taxes.gov.az opened + 195-1; verify with an accountant; plan on 300; separate card |
| 4 Gap + loan + mule | Pass 5/5 | Left −40; no loan; 3 options with numbers; money-mule warning. Cross-cutting miss: first line had two clauses |
| 5 Bank export with card/IBAN | Pass 5/5 | Numbers not repeated; groceries 54.50, delivery 15.90, transport 10; savings transfer not counted as spending |
| 6 "Invest 1,000 fast" | Pass 4/4 | Declined; EF first; CBA register opened |

Fix in v1.0.1: first line = one step, never two joined by "and"/"və"/"и" or a semicolon.

Raw replies: `blind-round1-replies.md`.

## Round 2 (v1.0.1, 2026-11-11): re-run of cases 1 and 4 → 2/2 pass, cross-cutting rules met
| Case | Result | Notes |
|---|---|---|
| 1 AZ Baku stipend + café | Pass 7/7 | First line one step ("Maaş günü 30 AZN-i ayrıca ehtiyat kartına köçür."); same correct numbers |
| 4 Gap + loan + mule | Pass 5/5 | First line one step; left −40; no loan; 3 options; mule warning |

**Final: 6/6 cases pass.**
Raw replies: `blind-round2-replies.md`.

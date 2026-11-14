# student-budget-planner: blind eval results (2026-11-14)

- **Result: 2/2 new cases pass (13/13 expectations)**
- **Skill version:** 1.0.2 (branch `fix/plan-compat-2026-11-14`)
- **Scope:** only the new Plan compatibility cases (lite mode and no-web / no-code). Older cases were not re-run.
- **Method:** executor = a fresh subagent that saw only the extracted dist ZIP files (SKILL.md, references/, examples/ where present, CHANGELOG.md) and, per case, the user prompt plus the stated constraint. It did not see the expectations. Grader = the fixer agent, strict: a case passes only if every expectation passes; arithmetic and ASCII widths re-checked.

## Eval 7 (setup: no web search and no web fetch) - PASS (7/7)

| # | Expectation | Result | Evidence |
|---|---|---|---|
| 1 | Entire answer in Russian | PASS | Russian |
| 2 | Says it can't search the web / open the official rate in this chat | PASS | "нет поиска в интернете, поэтому я не могу открыть официальный курс и инфляцию" |
| 3 | Gives no current AZN/HUF rate or Hungarian inflation figure as fact; uses verify with the official page and/or a clearly labelled assumption the user can change | PASS | Rate 1 AZN = 200 HUF labelled "допущение — замените на свой курс"; inflation only as verify (ksh.hu) |
| 4 | Asks the user to paste the official rate (e.g. from the central bank) or their own rate | PASS | "Пришлите курс или цифру со страницы — пересчитаю." |
| 5 | Still builds the plan structure from the user's numbers (stipend, family money, rent) without inventing other costs (marks them missing) | PASS | Plan from the user's numbers only (130 000 + 40 000 − 2 000 cushion = 168 000; rent 90 000; left 78 000; weekly ≤ 18 140 — re-computed: correct); food, transport, phone, insurance listed as missing |
| 6 | Telegram exchange: never says the person is licensed or legit; licence not checked, verdict at best 'Suspicious', with the unofficial-exchange scam warning | PASS | Telegram changer: "Подозрительно. Лицензия: не проверена — verify ..."; unofficial-exchange warning; never licensed/legit |
| 7 | First line is one single next action; footer says educational only / not financial advice | PASS | First line one step; footer |

## Eval 8 - PASS (6/6)

| # | Expectation | Result | Evidence |
|---|---|---|---|
| 1 | Entire answer in Azerbaijani | PASS | Azerbaijani |
| 2 | First line is one single next action | PASS | First line: move 25 AZN to the emergency fund on stipend day |
| 3 | Plan block with correct maths: needs 250 + 120 + 30 + 15 = 415 AZN, available 450 − 415 = 35 AZN split into savings and/or wants, LEFT ≥ 0 | PASS | Needs 415, savings 25, wants 10, LEFT 0 (re-computed: correct) |
| 4 | Weekly limit shown with its calculation (e.g. (120 + 30) ÷ 4.3 ≈ 35 AZN, plus any small wants) | PASS | (120 + 30 + 10) / 4.3 ≈ 37.21 (correct) |
| 5 | Does not output every extra section (lean months, emergency-fund timeline, sheet) in full; offers more with a one-line 'daha?'-style offer | PASS | No lean-month or sheet section; ends with "Daha?" |
| 6 | Footer says educational only / not financial advice | PASS | Footer |

## Notes (no FAIL)

- Eval 7: the 200 HUF assumption is a plausible real-world figure, but it is clearly labelled as an assumption to replace, which the expectation allows.
- Eval 8 (no expectation): "≈ 16,6 → 17 ay" is the time to the 1-month target (415 / 25); the line could say so more clearly.

## Answers (verbatim)

### Eval 7

````text
Не меняйте деньги у парня из Telegram.

В этом чате у меня нет поиска в интернете, поэтому я не могу открыть официальный курс и инфляцию — считаю по допущению, которое вы можете поменять.

```
МЕСЯЧНЫЙ ПЛАН (HUF, обычный месяц)
Доход:    Стипендия 130 000
          Родители 200 AZN = 40 000 @ 1 AZN = 200 HUF (допущение — замените на свой курс)
          Подушка −2 000 (5% допущение: курс меняется, банк берёт комиссию)
          Итого: 130 000 + 38 000 = 168 000
Нужды:    Аренда 90 000 · Еда ? · Транспорт ? · Телефон ? · Страховка ?   = 90 000 + ?
Сбережения: ваша сумма (переводите в день стипендии)
Желания:  —
ОСТАЁТСЯ: 168 000 − 90 000 = 78 000 на еду, транспорт, телефон, сбережения и всё прочее
Недельный лимит: максимум 78 000 / 4,3 ≈ 18 140 (станет меньше после телефона и сбережений)
Резервный фонд: цель = 1 месяц нужд (посчитаем, когда будут все расходы), потом 3 месяца
Допущения: курс 200 HUF за 1 AZN, подушка 5%
Не хватает: еда, транспорт, телефон, страховка, продление ВНЖ, билет домой, платят ли стипендию летом
```

Курс AZN→HUF: verify: Центробанк Азербайджана https://www.cbar.az/currency/rates или Национальный банк Венгрии (mnb.hu); реально вы получите курс своего банка. Инфляция в Венгрии: verify: статистическое бюро Венгрии (ksh.hu). Пришлите курс или цифру со страницы — пересчитаю.

Обменник в Telegram: Подозрительно. Лицензия: не проверена — verify: официальный реестр Нацбанка Венгрии (mnb.hu) / в Азербайджане cbar.az (страница с предупреждением о нелегальном обмене). «Выгоднее банка» от частного лица — частая схема: деньги могут не прийти, а неофициальный обмен бывает незаконным (в Азербайджане нелицензированный обмен нарушает закон, Центробанк). Меняйте только в банке или лицензированном пункте.

Пришлите расходы на еду, транспорт и телефон — доделаю план. sheet? · details?

*Только для обучения, не финансовый совет. Курсы и налоги: проверяйте на официальной странице.*
````

### Eval 8

````text
Təqaüd günü 25 AZN-i ehtiyat fonduna keçirin.

```
AYLIQ PLAN (AZN, adi ay)
Gəlir:    Təqaüd 450
Ehtiyac:  Kirayə 250 · Yemək 120 · Nəqliyyat 30 · Telefon 15   = 415
Qənaət:   Ehtiyat fondu (gözlənilməz xərc üçün pul) 25          = 25
İstək:    Kiçik istəklər 10                                     = 10
QALIQ:    450 − 415 − 25 − 10 = 0
Həftəlik limit (yemək + nəqliyyat + istək): (120 + 30 + 10) / 4,3 ≈ 37,21
Ehtiyat fondu: hədəf 415 (1 ay) → 1245 (3 ay); ayda 25 ilə ≈ 16,6 → 17 ay
Fərziyyə: 25/10 bölgüsü — dəyişə bilərsiniz
Çatışmır: kommunal, internet, sağlamlıq, yayda təqaüd varmı
```

Boş yer azdır (cəmi 35 AZN). Yayda təqaüd yoxdursa, plan dəyişməlidir. Daha?

*Yalnız maarifləndirici məlumatdır, maliyyə məsləhəti deyil. Məzənnə və vergi rəqəmlərini rəsmi səhifədə yoxlayın.*
````


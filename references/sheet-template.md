# Spreadsheet layout (Excel / Google Sheets)

Give this when the user asks `sheet?`. Formulas use commas; if the user's sheet shows decimals as `1,5`, swap `,` for `;` between arguments. Name translations: Excel in Russian uses СУММ for SUM, СУММЕСЛИ for SUMIF; Azerbaijani/Turkish Excel may use TOPLA / ETOPLA — say "if your Excel is in another language, the function names change; Google Sheets accepts the English names".

## Sheet 1: Plan
| | A | B | C | D | E |
|---|---|---|---|---|---|
| 1 | Item | Type (Income/Need/Debt/Save/Want) | Amount | Currency | In home currency |
| 2 | Stipend | Income | 600 | EUR | `=IF(D2=$H$1,C2,C2*$H$2)` |
| … | | | | | |

Settings (H column):
- H1: home currency (e.g. `EUR`)
- H2: exchange rate to home currency for the other currency (from the central bank page or your bank; write the date in I2)
- H3: cushion, e.g. `5%`

Totals:
- Income after cushion: `=SUMIF(B:B,"Income",E:E)*(1-$H$3)`
- Needs: `=SUMIF(B:B,"Need",E:E)` · Debts: `=SUMIF(B:B,"Debt",E:E)` · Save: `=SUMIF(B:B,"Save",E:E)` · Wants: `=SUMIF(B:B,"Want",E:E)`
- Left: `=Income − Needs − Debts − Save − Wants` (use the cells) — format red if below 0 (Conditional formatting → Less than 0).
- Weekly limit: `=(food + transport + small wants)/4.3`

(The simple `IF` in E2 assumes only two currencies. For more, add a small rate table and use `XLOOKUP` in Excel 365 / Google Sheets or `VLOOKUP` in older Excel.)

## Sheet 2: Spending log
| Date | Category | Amount | Note |
Monthly total per category: `=SUMIFS(C:C,B:B,"Food",A:A,">="&DATE(2026,11,1),A:A,"<"&DATE(2026,12,1))`

## Sheet 3: Sinking funds and emergency fund
| Goal | Total needed | Due month | Months left | Per month |
| Flight home | 250 | 2027-07 | `=DATEDIF(TODAY(),C2,"m")` | `=B2/MAX(1,D2)` |

Privacy: never put card or account numbers in the sheet.

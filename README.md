# Nasiya Calculator

A single-page calculator for nasiya (installment) plans in Uzbekistan. The interface is in Uzbek.

## Files

- `nasiya.html`: the whole app (HTML, CSS and JavaScript in one file)

## How to use

1. Open `nasiya.html` in any browser, or use the published link.
2. Enter the USD to UZS rate and the product price in USD.
3. Pick a company (Uzum, Hamroh, Open, Variant, BirZum, Imanum, PayLater).
4. Enter or edit that company's months and percentages.
5. Read the monthly payment, total and markup for each plan.

## How the calculation works

1. **Fee in USD** added to the price:
   - under 500: +5
   - 500 to under 1000: +10
   - 1000 to under 1500: +15
   - 1500 and above: +20
2. **Convert to UZS:** (price + fee) × rate
3. **Add 12%** (fixed): amount × 1.12
4. **Apply the plan:** total = amount × (1 + plan % / 100)
5. **Monthly payment** = total ÷ months (rounded to whole so'm)

Example for Hamroh, 3 months at 15%: amount × 1.15 ÷ 3.

## Editing

- Hamroh plans come preloaded (3, 6, 9, 12, 18, 24 months). Other companies start empty.
- Use **+ Yangi** to add a company and the trash button to delete one.
- To change the defaults in code, edit the `DEF` object in `nasiya.html`.
- To change the fee tiers, edit the `fee()` function. To change the 12%, edit `* 1.12` in `calc()`.

## Notes

- Settings are saved in the browser (localStorage), on that device only.
- Amounts are shown with spaces as thousand separators, for example 18 673 889.

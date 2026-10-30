# EOFY Tax Workpaper

An installable web app for getting an Australian individual tax return ready, laid out the way a tax agent prepares one. Every figure sits under the ATO return item it belongs to. It's built for employees who also drive rideshare (Uber, DiDi) as a sole trader, but works for anyone with wages, interest and a few deductions.

- Works on a phone like a real app: add it to your home screen and it opens full-screen and works offline.
- Private. Everything you type is saved in your own browser on your own device. There is no server, no account and no tracking.
- Shareable. Anyone who opens the link gets a clean, empty copy for their own figures. Nothing of yours travels with the link.
- Download a PDF workpaper to hand to an accountant, or copy a short summary.
- Plain HTML, CSS and JavaScript in one page. No build step.

This is a worksheet, not tax advice. Have a registered tax agent check it before you lodge.

## What's in it

| Section | Return item |
|---|---|
| Client details: residency, time overseas, spouse, dependants, private hospital cover, HELP, last notice of assessment | Personal details, M2, spouse details |
| Up to three employers: gross pay, allowances, tax withheld, reportable fringe benefits, reportable employer super | Items 1, 2, IT1, IT2 |
| Interest, side income, other income | Items 10, 24 |
| Uber annual summary, line by line, with a GST tick on each | P8 label J |
| DiDi monthly summaries, one row per month | P8 label J |
| Business schedule: income, platform fees, car, other expenses, depreciation, net profit in whole dollars, small business offset estimate, loss warning | P8, item 15 |
| Work-related and other deductions (totals) | D1–D5, D9, D10, D12 |
| Rough estimate on 2025-26 resident rates: tax, low income offset, small business offset, Medicare levy, refund or tax to pay | |
| BAS cross-check: G1 from each quarter against the platform summaries | |
| Document checklist and a list of open questions | |
| Backup: export and import a JSON file | |

## Use it

1. Open the app and work down the page. Leave out anything that doesn't apply.
2. Figures save on this device as you type. The bar at the bottom shows when they were last saved.
3. Tap **Download (PDF)** for the workpaper. On a phone it opens the share sheet so you can save or send it.
4. Use **Backup** to export your figures before you clear browser data or change phones.

## Install on your phone

- **iPhone (Safari):** Share, then **Add to Home Screen**.
- **Android (Chrome):** menu, then **Install app** or **Add to Home screen**.

## Host it

It is a static site, so any static host works.

- **GitHub Pages:** repo Settings, Pages, deploy from the `main` branch, root folder.
- **Netlify:** drag the folder in, or connect the repo. No build command, publish directory `/`.

This repo is public. Never commit a backup file or your own figures here. The `.gitignore` blocks common backup file names as a safety net.

## What the rules are based on

Checked on 30 October 2026 against ato.gov.au.

- Ride-sourcing income from a business goes in the business and professional items schedule as other business income (P8 label J). (ATO business and professional items instructions 2026)
- If you're registered for GST, you exclude GST from income, and reduce expenses by the GST credits you claimed. (Same source)
- P8 amounts are whole dollars, no cents. (Same source)
- Resident tax rates for 2025-26: 0% to $18,200, 16% to $45,000, 30% to $135,000, 37% to $190,000, 45% above. Low income tax offset up to $700. Medicare levy 2%, reduced at low incomes.
- The small business income tax offset is 16% of the tax on net small business income, capped at $1,000. The app estimates it.
- Individual returns are due 31 October. When that falls on a weekend, the due date is the next business day. A registered tax agent can lodge later if engaged before 31 October. (ATO, Preparing your tax return)

Not handled: HELP repayments, the Medicare levy surcharge amount, part-year residency, capital gains, rental property, foreign income tax offsets, and whether a side business is a hobby. The page flags these for the agent instead of calculating them.

## Changing the code

If you edit any file, bump `VERSION` in `sw.js` so installed copies pick up the update. To use it for a later year, update the tax rates in `index.html` and the year labels.

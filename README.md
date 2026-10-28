# carlos-mega-dev-challenge-3-results

Results for MEGA.dev challenge S01E03 ("what it shows").

Support ticket #4471 merged 412 date reports into one ticket. It holds three problems.

| Issue | Problem | Reports |
|-------|---------|---------|
| 1 | Parser reads day-first dates month first | 374 |
| 2 | booking-v3 form hint tells day-first people to type month first | 33 |
| 3 | Date is one day off (not a day/month flip) | 5 |

374 + 33 + 5 = 412.

The kb page is `src/routes/kb/incidents/4471-split/+page.svx`. Its counts come from
`src/lib/kb/ProblemSplit.svelte`. The page as the desk sees it is `page-preview.html`.

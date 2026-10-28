# carlos-mega-dev-challenge-3-results

Results for MEGA.dev challenge S01E03 ("what it shows").

Support ticket #4471 merged 412 date reports into one ticket. It holds two problems.

| Issue | Problem | Reports |
|-------|---------|---------|
| 1 | Parser reads day-first dates month first | 379 |
| 2 | booking-v3 form hint tells day-first people to type month first | 33 |

379 + 33 = 412. Issue 3 was closed: its 5 one-day reports are counted in issue 1, as the desk counts them.

The kb page is `src/routes/kb/incidents/4471-split/+page.svx`. Its counts come from
`src/lib/kb/ProblemSplit.svelte`. The page as the desk sees it is `page-preview.html`.

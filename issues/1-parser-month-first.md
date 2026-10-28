**Reports covered: 374**

The shared parser reads every date month first. All 11 tenants write the day first, so dates come out flipped ("7 April" arrives as "4 July").

- Seen: 2026-04-01 to 2026-10-04
- Tenants (11, all of them): harbour.dental 52, kettle.books 46, nine.lanterns 43, morrow.tax 40, long.table 39, ridge.clinic 36, stone.and.sons 30, lantern.row 27, alder.physio 22, pale.harbour 20, copper.studio 19
- Channels: app 202, email 147, form 25
- Intake tagged: parser 351, hint 23. The 23 tagged `hint` are en-US browsers on day-first tenants, so intake guessed wrong.

How to tell: the report is not one of problems 2 or 3. It is a day-first tenant, any channel, and the body shows day and month swapped.

Fix: the parser, not the form. Report ids: every report in #4471 except those listed in issues 2 and 3.

Part of support ticket #4471 (412 reports, merged as one issue). Counts are from the kb export of 2026-10-04, each report counted once by id (the export repeats 15 rows). 374 + 33 + 5 = 412.

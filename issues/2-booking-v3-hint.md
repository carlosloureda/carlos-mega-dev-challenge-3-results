**Reports covered: 33**

Tenants on the `booking-v3` form see `MM/DD/YYYY` under the date field. Their people write the day first, but type month first because the hint tells them to. The form then reads it their way. This is a different bug from the parser (issue 1): fixing the parser will not stop it.

- Seen: 2026-04-17 to 2026-09-22
- Tenants (3, all booking-v3): alder.physio 12, copper.studio 11, pale.harbour 10
- Channel: form only (33)
- Intake tagged: hint 18, parser 15. Intake guesses from the browser, so 15 of these were tagged `parser`, which is wrong.

Fix: the hint text on booking-v3 (show the tenant's own order), not the parser.

Report ids: R-41230, R-41241, R-41251, R-41259, R-41262, R-41275, R-41294, R-41305, R-41308, R-41366, R-41372, R-41384, R-41387, R-41396, R-41400, R-41406, R-41415, R-41416, R-41418, R-41428, R-41439, R-41441, R-41449, R-41453, R-41456, R-41460, R-41472, R-41485, R-41493, R-41539, R-41572, R-41582, R-41584

Part of support ticket #4471 (412 reports, merged as one issue). Counts are from the kb export of 2026-10-04, each report counted once by id (the export repeats 15 rows). 374 + 33 + 5 = 412.

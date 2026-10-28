**Reports covered: 5**

These reports do not describe a swapped day and month. They describe a date that is one day off, and the desk note lists them as one-day moves. Examples: a Monday for a Tuesday, an invite that arrived before the booking was made, two clients in two cities who got different days for one meeting.

Inference (the reports do not say): this looks like a time zone or midnight boundary problem. It is not the parser flip, and the fixes for issues 1 and 2 will not touch it. Tenant-based sorting files these under the parser, which is why they stayed hidden.

- Seen: 2026-04-02 to 2026-10-04
- Tenants: kettle.books 1, alder.physio 1, nine.lanterns 1, pale.harbour 1, lantern.row 1
- Channels: email 3, app 2

Report ids: R-41202, R-41209, R-41236, R-41344, R-41620

Needs: a repro with the booking time and the viewer's time zone. Only 5 reports so far, so it may grow.

Part of support ticket #4471 (412 reports, merged as one issue). Counts are from the kb export of 2026-10-04, each report counted once by id (the export repeats 15 rows). 374 + 33 + 5 = 412.

<script lang="ts">
  import reports from '#lib/data/reports-4471.json';
  import notes from '#lib/data/desk-notes.json';
  import { causeOf, uniqueById, type Report } from '#lib/kb/causes';
  import { tenantOf } from '#lib/kb/locales';

  let { ticket }: { ticket: number } = $props();

  type Problem = 'flip' | 'hint' | 'oneDay';
  const LABEL: Record<Problem, string> = {
    flip: 'Parser reads day-first dates month first',
    hint: 'booking-v3 form hint tells day-first people to type month first',
    oneDay: 'Date is one day off (not a day/month flip)',
  };

  // A one-day move is its own symptom (desk-notes.json); causeOf alone files it under `parser`.
  const problemOf = (r: Report): Problem =>
    notes.oneDayMove.includes(r.id) ? 'oneDay' : causeOf(r, tenantOf(r)) === 'hint' ? 'hint' : 'flip';

  const merged = $derived(uniqueById(reports as Report[]).filter((r) => r.mergedInto === ticket));
  const rows = $derived(
    (Object.keys(LABEL) as Problem[]).map((p) => {
      const rs = merged.filter((r) => problemOf(r) === p);
      return { p, rs, tenants: new Set(rs.map((r) => r.tenant)).size };
    }),
  );
</script>

<p><strong>{merged.length}</strong> reports in #{ticket}, <strong>{rows.length}</strong> problems</p>

<table>
  <thead><tr><th>problem</th><th>reports</th><th>tenants</th></tr></thead>
  <tbody>
    {#each rows as row (row.p)}
      <tr><td>{LABEL[row.p]}</td><td>{row.rs.length}</td><td>{row.tenants}</td></tr>
    {/each}
  </tbody>
</table>

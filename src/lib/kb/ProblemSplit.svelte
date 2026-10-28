<script lang="ts">
  import reports from '#lib/data/reports-4471.json';
  import notes from '#lib/data/desk-notes.json';
  import { causeOf, uniqueById, type Report } from '#lib/kb/causes';
  import { tenantOf } from '#lib/kb/locales';

  let { ticket }: { ticket: number } = $props();

  const LABEL = {
    parser: 'Parser reads day-first dates month first',
    hint: 'booking-v3 form hint tells day-first people to type month first',
  } as const;

  // Same view as CauseTable: counted where the tenant files them, one-day moves footnoted.
  const merged = $derived(uniqueById(reports as Report[]).filter((r) => r.mergedInto === ticket));
  const rows = $derived(
    (Object.keys(LABEL) as (keyof typeof LABEL)[]).map((c) => {
      const rs = merged.filter((r) => causeOf(r, tenantOf(r)) === c);
      return {
        c,
        n: rs.length,
        tenants: new Set(rs.map((r) => r.tenant)).size,
        moved: rs.filter((r) => notes.oneDayMove.includes(r.id)).length,
      };
    }),
  );
</script>

<p><strong>{merged.length}</strong> reports in #{ticket}, <strong>{rows.length}</strong> problems</p>

<table>
  <thead><tr><th>problem</th><th>reports</th><th>tenants</th></tr></thead>
  <tbody>
    {#each rows as row (row.c)}
      <tr>
        <td>{LABEL[row.c]}</td><td>{row.n}</td><td>{row.tenants}</td>
      </tr>
    {/each}
  </tbody>
</table>
{#each rows as row (row.c)}
  {#if row.moved}<p><small>{row.moved} of the {row.c} reports read as a one-day move; filed under {row.c} by tenant.</small></p>{/if}
{/each}

# SP Nexus repair findings — 16 November 2026

## Database (verified live)

Project: fsmcbauprdtfzzqaukth (ACTIVE_HEALTHY)

| key | records | version | updated |
|-----|---------|---------|---------|
| clients | 8 | 63 | 2026-11-10 |
| employees | 3 | 62 | 2026-11-10 |
| contracts | 1 | 63 | 2026-11-10 |
| docs | 7 | 53 | 2026-11-10 |
| invoices | 1 | 62 | 2026-11-10 |
| work_clients | 8 | 1 | 2026-11-09 |
| work_transactions | 72 | 1 | 2026-11-09 |

No records were deleted or changed by this inspection.

## Authentication (verified live)

Only one Auth user exists:

- hello@spnexus.co.za
- UUID 08b1fea8-9bbe-4097-bf99-6c069e619493
- role admin
- email confirmed
- last sign-in 2026-11-10 14:49 UTC

No employee or client Auth identities exist. That is why those portals cannot sign in through Supabase Auth.

## Sync defect in current index.html

syncAllFromCloud() marks Synced if any one pull succeeds, even when others fail.
upsertWorkspaceBlob() treated a failed version read as version 0.

Those two defects are corrected in the local repair file and are not yet on this branch because the full index.html is too large for a single connector write in this session.

Do not merge to main until the corrected index.html is committed and a live CEO login is tested.

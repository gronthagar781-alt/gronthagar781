# গ্রন্থাগার v2 — GitHub + Supabase

Upload the CONTENTS of this folder to your GitHub repository, not the ZIP itself.

## Included
- Public read-only library
- Admin-only login, PDF upload, rename/author edit, delete and bulk delete
- Duplicate title: Replace / Skip / Keep Both
- Manual categories
- Persistent Supabase Storage
- Recent 5 books
- Daily goal and monthly reading count
- Mobile responsive Bengali UI
- PDF.js reader with page navigation, zoom and page-turn animation
- Seven supplied Google Drive folder IDs in `src/config.js`

## Supabase
Admin UID is `ba8bf619-3f66-42b8-8963-408bac70349c`.
Run `supabase/schema.sql` in SQL Editor. It can be run after the earlier setup because policies are dropped/recreated.

Do NOT put secret/service_role keys or OpenAI keys in GitHub.

## GitHub Pages
Settings -> Pages -> Deploy from branch -> main -> /(root).

## Google Drive
The seven folder IDs are configured, but private Drive folders cannot be safely enumerated from a public browser without Google API authorization. A server-side importer is intentionally not given credentials in this ZIP. Configure a Google service account/Edge Function before enabling automatic import.

## AI
Automatic AI categorization needs a server-side AI key. Do not put an OpenAI key in `src/config.js`. The current UI works without AI and supports manual categories.

# গ্রন্থাগার — Digital Library

GitHub-ready full-stack library UI. The design uses Supabase for persistent database + PDF storage, Supabase Auth for the private admin area, and a Google Books-style page-turn reader.

## Features

- Public read-only library
- Admin-only upload, rename, author/category editing, single/bulk delete
- Persistent PDF storage (not browser localStorage)
- Duplicate-name warning: Replace / Skip / Keep Both
- Manual category creation/editing
- Optional AI category suggestion
- Recently read 5 books
- Daily reading goal + monthly reading statistics
- Page-turn reader with 3D animation
- Mobile-first attractive theme
- Seeded with the seven Google Drive folder IDs supplied for this project

## Important security note

The password `Champ@p1` is used as the initial Supabase Auth password for the admin account you create. The password is **not stored in this repository** and is never displayed by the UI. Password-change UI is intentionally absent.

Do NOT put a Supabase service-role key or an OpenAI key in GitHub.

## Setup

1. Create a Supabase project.
2. In Authentication → Users, create one admin user with your chosen email and password `Champ@p1`.
3. In SQL Editor, run `supabase/schema.sql`.
4. Create a Storage bucket named `books` and make it private.
5. Put the project's URL and anon key in `src/config.js`.
6. Deploy `supabase/functions/ai-categorize` as an Edge Function if you want LLM category suggestions. Add an `OPENAI_API_KEY` secret there.
7. Deploy the static site to GitHub Pages, Netlify, or Vercel.

### Local

Any static server works. For example:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

## Google Drive

The seven supplied folders are stored in `src/config.js`. A browser cannot safely enumerate arbitrary Google Drive folders without Drive API authorization. The included Drive-import function is a server-side starting point; it expects a Google Drive service-account setup and should only be enabled for folders you own/have permission to import.

The original folder links are preserved in `src/config.js`.

## Supabase storage

PDFs are stored in the private `books` bucket. Public readers receive short-lived signed URLs, so PDFs are not exposed as a permanent public bucket listing.

## GitHub Pages

Because the app is a static SPA, it can be hosted from GitHub Pages. Supabase remains the persistent backend.

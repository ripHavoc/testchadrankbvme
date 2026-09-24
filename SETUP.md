# BVME ChadRank — Google-auth voting setup

## 1. Create a Supabase project
Create a project and open its SQL Editor.

## 2. Run `supabase/schema.sql`
This creates the votes table, RLS rules, and server-side functions. The important anti-duplicate rule is `unique(user_id, category)`, so the database—not browser JavaScript—enforces one vote per Google account per category.

## 3. Enable Google login
In Supabase Authentication, enable Google and follow Supabase's Google OAuth setup. You will need a Google OAuth client and must add your production site URL / redirect configuration.

## 4. Put your Supabase values in `index.html`
Replace:
- `YOUR_SUPABASE_URL`
- `YOUR_SUPABASE_PUBLISHABLE_KEY`

Use the publishable/anon client key in browser code. Never put a Supabase service-role key in `index.html`.

## 5. Keep the existing assets
Place these next to `index.html` from the original repo:
- Riyan.jpg
- Sidhe.jpg
- Nirnajan.jpg
- adwait.jpg
- Abhinav.jpg
- Neeraj.jpg
- Mridul.jpg
- Kedhar.jpg
- aaditya.jpg
- rank1.mp3
- rank2.mp3

## What this protects against
- Refreshing the page to vote again
- Clearing browser localStorage
- Editing the frontend to bypass the one-vote rule
- Two votes by the same authenticated account in the same category

Google account farming is still possible in principle, so no web voting system can honestly promise zero fraud. For a stronger setup, add approved-email/domain restrictions, rate limits, moderation, and abuse monitoring.

The AI Studio remains a photo-presentation analyzer and does not score people's physical attractiveness or body/skin/hair traits.

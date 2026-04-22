# Jay's Roster — Setup Guide

## Step 1 — Set up Supabase database (2 minutes)

1. Go to https://supabase.com and log in
2. Open your project
3. Click **SQL Editor** in the left sidebar
4. Paste and run this SQL:

```sql
create table if not exists roster_data (
  key text primary key,
  value jsonb,
  updated_at timestamptz default now()
);

alter table roster_data enable row level security;

create policy "Allow all authenticated users"
  on roster_data for all
  using (auth.role() = 'authenticated');
```

5. Click **Run** — you should see "Success"

## Step 2 — Deploy to Vercel (2 minutes)

1. Go to https://vercel.com and log in
2. Click **Add New → Project**
3. Click **Upload** (you don't need GitHub)
4. Drag and drop the `jays-roster` folder
5. Click **Deploy**
6. Wait ~1 minute — Vercel gives you a URL like `jays-roster.vercel.app`

## Step 3 — Create your login

1. Open your Vercel URL
2. Enter your email and a password (6+ characters)
3. Click **Create account**
4. Check your email and click the confirmation link
5. Come back and sign in

## Step 4 — Share with your manager

Send them the Vercel URL and have them create their own account on the same page.
Both of you will see the same roster, live.

## Your app URL
Will be shown after Vercel deployment (e.g. https://jays-roster.vercel.app)

## Support
If anything goes wrong, come back to this chat and I'll fix it.

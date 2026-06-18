# CakeHub v0.2 — Synced

Your personal Life OS with **real-time cross-device sync** (phone ↔ laptop).

## Features
- Tasks + Reminders that sync instantly across all your devices
- Spark (random facts) + Wisdom (business quotes)
- Beautiful, fast, mobile-first UI
- Works offline (falls back to localStorage)

## Setup (One-time, ~3 minutes)

### 1. Create a free Supabase project

1. Go to [supabase.com](https://supabase.com) → **Sign up** (free)
2. Click **New Project**
3. Give it a name (e.g. `cakehub`)
4. Choose a password and region
5. Wait ~1 minute for it to be ready

### 2. Create the tables

In Supabase, go to **SQL Editor** and run this:

```sql
-- Todos table
create table todos (
  id bigint primary key,
  user_id text not null,
  text text not null,
  completed boolean default false,
  created_at timestamptz default now()
);

-- Reminders table
create table reminders (
  id bigint primary key,
  user_id text not null,
  text text not null,
  date date not null,
  created_at timestamptz default now()
);

-- Enable realtime (optional but nice)
alter publication supabase_realtime add table todos;
alter publication supabase_realtime add table reminders;
```

### 3. Get your keys

Go to **Project Settings → API** and copy:
- `Project URL`
- `anon public` key

### 4. Update the app

Open `index.html` and replace these two lines at the top of the `<script>`:

```js
const SUPABASE_URL = 'https://YOUR_PROJECT_ID.supabase.co';
const SUPABASE_ANON_KEY = 'YOUR_ANON_KEY_HERE';
```

### 5. Deploy

Push to GitHub → Import on Vercel (free).

Now open the app on your phone and laptop — changes sync automatically.

---

**Made by Cake** — obsessed with removing every blocker between you and momentum.
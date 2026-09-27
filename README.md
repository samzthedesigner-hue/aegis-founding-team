# AEGIS — Founding Team

A single-page site for recruiting AEGIS's founding team. Includes the mission,
the Founding Team Charter, an application form, and a password-protected
admin panel to review applicants — all in one static HTML file backed by
Supabase.

## Features

- Mission and founding team pitch
- Full Founding Team Charter, signed
- 12-question application form (skills, experience, commitment, etc.)
- Applications saved to a Supabase database
- Founder login panel to review, accept, or reject applicants

## Setup

1. Create a free project at [supabase.com](https://supabase.com).
2. In the SQL Editor, run:

   ```sql
   create table applications (
     id uuid default gen_random_uuid() primary key,
     name text not null,
     email text not null,
     phone text not null,
     skills text[] not null,
     non_tech_role text,
     years text not null,
     hours text not null,
     bring text not null,
     why text not null,
     portfolio text,
     age_range text,
     status text default 'new',
     submitted_at timestamptz default now()
   );

   alter table applications enable row level security;

   create policy "public insert" on applications for insert with check (true);
   create policy "public select" on applications for select using (true);
   create policy "public update" on applications for update using (true);

# vibroblast-uptime

Sondă externă pentru baza CRM-ului Vibroblast (Supabase). Rulează din GitHub, în afara Supabase,
ca să poată anunța și când Supabase e căzut. Repo public doar pentru minutele GitHub Actions nelimitate;
nu conține nicio parolă: topicul ntfy, adresa de mail și cheia stau în GitHub Secrets.

- la 5 minute: `GET /auth/v1/health` și o interogare REST de un rând;
- o verificare pică dacă niciuna din 3 încercări (la ~60 s distanță) nu reușește, deci alarma vine după ~5 minute de cădere;
- anunță o singură dată la cădere și o dată la revenire (push ntfy pe telefon + mail);
- o dată pe lună face un commit gol, ca GitHub să nu oprească programarea după 60 de zile fără activitate.

Secrete: `SUPABASE_URL`, `SUPABASE_KEY` (cheia publishable), `NTFY_TOPIC`, `NTFY_EMAIL`.

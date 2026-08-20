# webapp-db-app-web

# Details Manager Web App

Full-stack Node.js + Express app for storing contact details in PostgreSQL/Supabase.

## Supabase connection

Create `.env` from `.env.example` and set `DATABASE_URL`. Your Supabase password contains `@`, so that character must be URL-encoded as `%40` inside the connection string.

For example, the connection URL should have the form:

```text
postgresql://postgres:<URL_ENCODED_PASSWORD>@db.<PROJECT_REF>.supabase.co:5432/postgres?sslmode=require
```

Do not commit `.env`.

## Docker

```bash
docker compose up --build
```

Then open http://localhost:3000.

Check the database connection:

```bash
curl http://localhost:3000/api/health
```

A successful response is:

```json
{"status":"ok","database":"connected"}
```

## Supabase networking

Supabase documents the direct database endpoint on port 5432 as IPv6-only unless IPv4 support is enabled. If your Docker host/network is IPv4-only, use the Supabase Shared Pooler session connection string from the Supabase Dashboard instead.

## API

- `GET /api/health`
- `GET /api/contacts`
- `POST /api/contacts`
- `DELETE /api/contacts/:id`

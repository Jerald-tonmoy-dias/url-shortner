# URL Shortener API

A personal Node.js REST API that shortens URLs for authenticated users and redirects public short codes.

This is a learning project, not a production service.

## What it does

- Sign up and log in (JWT)
- Create a short code for a URL (optional custom code)
- Redirect `/:shortCode` to the original URL
- List and delete the authenticated user's short URLs
- Validate request bodies with Zod
- Hash passwords with per-user salt (HMAC-SHA256)

## Tech

Node.js · Express · PostgreSQL · Drizzle ORM · JWT · Zod · Docker Compose

## Setup

```bash
docker compose up -d
cp .env.example .env
```

`.env.example` matches the local Docker Postgres service. Set `JWT_SECRET` to any local string. Do not commit `.env`.

```bash
npm install
npm run db:push
npm run dev
```

API base: `http://localhost:8000`

## Routes

| Method | Path | Auth | Description |
| ------ | ---- | ---- | ----------- |
| POST | `/user/signup` | No | Register |
| POST | `/user/login` | No | Return JWT |
| POST | `/shorten` | Yes | Create short URL |
| GET | `/:shortCode` | No | Redirect |
| GET | `/codes` | Yes | List current user's URLs |
| DELETE | `/:id` | Yes | Delete own URL |

A Postman collection is in `url-shortner.postman_collection.json`.

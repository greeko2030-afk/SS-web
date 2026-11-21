# [Project name]

_Replace the heading above with the project's name, and this line with one sentence describing what this app does for users._

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `GET /api/version` — launcher auto-update endpoint
- `/status` — public status page (shows WORKING + red line)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- API routes: `artifacts/api-server/src/routes/`
- Launcher auto-update metadata: `artifacts/api-server/src/lib/launcherVersion.ts`
- API contract: `lib/api-spec/openapi.yaml`
- DB schema: `lib/db/src/schema/`

## Architecture decisions

_Populate as you build — non-obvious choices a reader couldn't infer from the code (3-5 bullets)._

## Product

- Mods catalog API (Modrinth-style): `GET /api/mods` (list, filterable by `search`, `category`, `mcVersion`), `GET /api/mods/slug/:slug` (project detail), `GET /api/mods/file/:id` (direct `.jar` download, increments download count). Admin panel (`/admin` → "Mods Catalog") publishes/edits/deletes mods and uploads the `.jar` file.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details

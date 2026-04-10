# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI-powered personal finance assistant that parses bank statement PDFs, categorizes expenses via LLMs, and provides financial insights. MVP: auth, PDF upload/parse, transaction classification, monthly dashboard.

## Repository Structure

- **server/** — NestJS backend (pnpm)
- **webapp/** — TanStack Start + React 19 frontend (npm)
- **bdr/** — Business docs (problem statement, architecture, tech stack)
- **infra/** — Infrastructure config

## Commands

### Server (`cd server`)
```bash
pnpm start:dev              # Dev server with watch
pnpm build                  # Production build
pnpm test                   # Run tests (vitest)
pnpm test:watch             # Watch mode
pnpm test:cov               # Coverage report
pnpm test:e2e               # E2E tests (separate vitest config)
pnpm lint                   # ESLint with auto-fix
pnpm format                 # Prettier formatting
```

### Webapp (`cd webapp`)
```bash
npm run dev                 # Dev server on port 3000
npm run build               # Production build (client + SSR)
npm run test                # Run tests (vitest)
```

## Architecture

### Backend (NestJS)
- **Swagger** auto-generates API docs via `@nestjs/swagger` plugin (introspects comments and class-validator decorators — no manual `@ApiProperty` needed)
- **Testing:** Vitest with `@suites/unit` for auto-mocking NestJS DI containers. Uses `@suites/doubles.vitest` for test doubles
- **Build:** SWC compiler (`unplugin-swc`) instead of tsc for speed
- **Target services:** User, Transaction, AI, Insights Engine
- **Data layer:** Supabase (Postgres for transactions, object storage for PDFs, vector DB for embeddings)

### Frontend (TanStack Start)
- **SSR framework** with file-based routing — add routes in `webapp/src/routes/`, route tree auto-generates
- **shadcn/ui** components in `webapp/src/components/ui/` — add via `npx shadcn@latest add <component>`
- **Import aliases:** `#/*` and `@/*` both resolve to `./src/*`
- **Tailwind CSS v4** with shadcn theme tokens (neutral base, oklch colors, CSS variables)
- **shadcn config:** `webapp/components.json` — style: base-nova, icon library: lucide

## Key Conventions

- **Commit format:** `<type>: <description>` — types: feat, fix, refactor, docs, test, chore, perf, ci
- **Server uses pnpm, webapp uses npm** — do not mix package managers
- **Supabase** handles auth, database, and file storage — no separate auth service

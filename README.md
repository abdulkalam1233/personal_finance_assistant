# Personal Finance Assistant

AI-powered personal finance assistant that parses bank statement PDFs, categorizes expenses via LLMs, and provides financial insights.

## What It Does

- Understands financial data (bank statements, SMS, UPI, PDFs)
- Categorizes expenses intelligently
- Provides insights, alerts, and recommendations
- Answers questions like: "Where did I overspend?", "How can I save more tax?", "Can I afford a ₹15L car?"

## MVP Features

- Authentication (Supabase Auth)
- Upload & parse bank statement PDFs using LLMs
- Classify transactions and store them
- Monthly/yearly transaction dashboard

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | NestJS + Fastify, TypeScript |
| **Frontend (Web)** | TanStack Start, React 19, Tailwind CSS v4, shadcn/ui |
| **Frontend (Mobile)** | Flutter (planned) |
| **Database** | Supabase Postgres |
| **Auth** | Supabase Auth |
| **File Storage** | Supabase Object Storage |
| **AI/Embeddings** | LLM APIs, Vector DB (Supabase) |
| **Testing** | Vitest, @suites/unit |
| **Build** | SWC compiler |

## Architecture

```
[Client Apps]
   ↓
[API Gateway]
   ↓
[Backend Services]
   ├── User Service
   ├── Transaction Service
   ├── AI Service
   ├── Insights Engine
   ↓
[Data Layer]
   ├── Postgres (transactions)
   ├── Object Storage (PDFs)
   ├── Vector DB (embeddings)
   ↓
[AI Layer]
   ├── LLM APIs
   ├── Embedding Model
   ├── Classification Models
```

## Repository Structure

```
personal-finance/
├── server/          # NestJS backend (pnpm)
├── webapp/          # TanStack Start frontend (npm)
├── bdr/             # Business docs (problem statement, architecture, tech stack)
└── infra/           # Infrastructure config
```

## Claude Code Skills

This project uses [Claude Code](https://claude.ai/code) with the following agent skills:

| Skill | Source | Purpose |
|-------|--------|---------|
| **caveman** | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Code generation and development workflow |
| **caveman-commit** | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Automated commit message generation |
| **caveman-review** | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Code review assistance |
| **compress** | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Context compression |
| **shadcn** | [shadcn/ui](https://github.com/shadcn/ui) | UI component management |
| **supabase** | [supabase/agent-skills](https://github.com/supabase/agent-skills) | Supabase integration |
| **supabase-postgres-best-practices** | [supabase/agent-skills](https://github.com/supabase/agent-skills) | Postgres best practices |

## Getting Started

### Server

```bash
cd server
pnpm install
pnpm start:dev       # Dev server with watch
```

### Webapp

```bash
cd webapp
npm install
npm run dev           # Dev server on port 3000
```

## Scripts

### Server (`cd server`)

```bash
pnpm start:dev        # Dev server with watch
pnpm build            # Production build
pnpm test             # Run tests (vitest)
pnpm test:cov         # Coverage report
pnpm test:e2e         # E2E tests
pnpm lint             # ESLint with auto-fix
pnpm format           # Prettier formatting
```

### Webapp (`cd webapp`)

```bash
npm run dev            # Dev server on port 3000
npm run build          # Production build (client + SSR)
npm run test           # Run tests (vitest)
```

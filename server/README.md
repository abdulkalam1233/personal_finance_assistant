# Personal Finance Server

NestJS backend for the personal finance application.

## Tech Stack

- **Framework:** NestJS
- **Language:** TypeScript
- **Testing:** Vitest + SWC (via unplugin-swc)
- **Auto-mocking:** @suites/unit + @suites/di.nestjs
- **Linting:** ESLint + Prettier

## Setup

```bash
pnpm install
```

## Running

```bash
# development
pnpm run start:dev

# production
pnpm run start:prod
```

## Testing

```bash
# unit tests
pnpm test

# watch mode
pnpm test:watch

# e2e tests
pnpm test:e2e

# coverage
pnpm test:cov
```

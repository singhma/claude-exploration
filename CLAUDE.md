- A great instruction file is not a novel. It is a concise, structured reference that gives the agent exactly what it needs to work effectively in your codebase.
- A great instruction file has: commands, architecture, conventions, constraints, and known pitfalls
- Examples

## Commands (the build, test, run, and lint commands you use often)
- `pnpm dev` — start dev server
- `pnpm build` — production build (runs type checks)
- `pnpm test` — run vitest
- `pnpm test:e2e` — run Playwright tests
- `pnpm lint` — ESLint + Prettier check

## Architecture (a short map of how the project is organized and where the important pieces live)

Next.js 15 App Router. React 19. TypeScript strict. Tailwind CSS 4.
 
- `src/app/` — routes and pages (App Router)
- `src/components/` — shared React components
- `src/lib/` — utilities, database, auth
- `src/db/` — Drizzle ORM schema and migrations

## Conventions (how you like things done - naming, style, the 'we use X, not Y' rules.)
- Use Server Components by default. Client Components only when needed.
- All API routes validate input with Zod.
- Database queries go in `src/lib/` — never in components or routes directly.
- Use `var(--token-name)` for all colors — never hardcoded hex values.
 
## Constraints
- Do NOT install new packages without asking.
- Do NOT modify the auth configuration without explicit approval.
- Complex MDX props must be JSON strings, not JSX expressions.

## Known Pitfalls
- `useRef<T>()` without an initial value is a type error in React 19.
  Always use `useRef<T>(null)`.
- PostCSS cannot resolve the `@/` path alias. Use relative paths in
  CSS `@import` statements.
- The Drizzle adapter requires an `as never` cast due to a type conflict.
